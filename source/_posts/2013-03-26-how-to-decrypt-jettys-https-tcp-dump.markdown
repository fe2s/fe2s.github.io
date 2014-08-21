---
layout: post
title: "How to decrypt jetty's https tcp dump"
date: 2013-03-26 16:22:03 +0300
comments: true
categories: https jetty ssl tcp
---

If you want to capture jetty's tcp dump of https and analyze encrypted packets later - here is an instruction. Applies for Jetty 7, not sure if the same works for other versions.

<!-- more -->


**Step 1.** Find obfuscated password in jetty.xml, it should start with OBF: prefix. Run it through the following deobfuscating function which I found in jetty sources.

```java
	public class Password {
	    public static final String __OBFUSCATE = "OBF:";

	    public static String deobfuscate(String s) {
		if (s.startsWith(__OBFUSCATE)) s = s.substring(4);

		byte[] b = new byte[s.length() / 2];
		int l = 0;
		for (int i = 0; i < s.length(); i += 4) {
		    String x = s.substring(i, i + 4);
		    int i0 = Integer.parseInt(x, 36);
		    int i1 = (i0 / 256);
		    int i2 = (i0 % 256);
		    b[l++] = (byte) ((i1 + i2 - 254) / 2);
		}

		return new String(b, 0, l);
	    }
	}
```

**Step 2.** Now you should have the password for keystore. The location of keystore should be listed in jetty.xml. Import keys to intermediate PKCS12 format

    $ /usr/java/jdk1.6.0_13/bin/keytool -importkeystore -srckeystore $YOUR_PATH_HERE/keystore -destkeystore intermediate.p12 -deststoretype PKCS12

**Step 3**. Extract RSA key from PKCS12

    $ openssl pkcs12 -in intermediate.p12  -nocerts -nodes -passin pass:$YOUR_PASS_HERE | openssl rsa -out privateRSAKey.pem

**Step 4.** Now you are good to feed wireshark or other preferred tool with RSA key.


