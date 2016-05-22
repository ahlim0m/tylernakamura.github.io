---
layout: post
title: "md5-checksums-Java"
date: 2016-05-21 16:52
comments: false
categories: md5 checksum java example class code
---
Below is a solution for generating MD5 Checksums in Java.
Credit goes to [Stack Overflow post](http://stackoverflow.com/a/304275/4143925).
It is a lengthy solution for a seemingly simple task.
This is the nature of Java I suppose.

```java
import java.io.*;
import java.security.MessageDigest;

public class MD5Checksum
{
	public static byte[] createChecksum(String filename) throws Exception
	{
		InputStream fis =  new FileInputStream(filename);

		byte[] buffer = new byte[1024];
		MessageDigest complete = MessageDigest.getInstance("MD5");
		int numRead;

		do
		{
			numRead = fis.read(buffer);
			if (numRead > 0) 
			{
				complete.update(buffer, 0, numRead);
			}
		} while (numRead != -1);

		fis.close();
		return complete.digest();
	}

	// a byte array to a HEX string
	public static String getMD5Checksum(String filename) throws Exception 
	{
		byte[] b = createChecksum(filename);
		String result = "";

		for (int i=0; i < b.length; i++) 
		{
			result += Integer.toString( ( b[i] & 0xff ) + 0x100, 16).substring( 1 );
		}
		return result;
	}
}
```
