# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.
diff -u -r ../Python-2.7.10/setup.py ./setup.py

--- ../Python-2.7.10/setup.py	2015-05-23 12:09:25.000000000 -0400+++ ./setup.py	2015-11-07 17:34:53.020310751 -0500

@@ -294,6 +294,9 @@

                           (ext.name, sys.exc_info()[1]))

             self.failed.append(ext.name)

             return

+

+	return # Skip import check which does not work when cross compiling

+

         # Workaround for Mac OS X: The Carbon-based modules cannot be

         # reliably imported into a command-line Python

         if 'Carbon' in ext.extra_link_args:

@@ -674,7 +677,8 @@

 

         # Lance Ellinghaus's syslog module

         # syslog daemon interface

-        exts.append( Extension('syslog', ['syslogmodule.c']) )

+        # Termux: Add 'log' android library since we use android logging:

+        exts.append( Extension('syslog', ['syslogmodule.c'], libraries=['log']) )

 

         # George Neville-Neil's timing module:

         # Deprecated in PEP 4 http://www.python.org/peps/pep-0004.html
