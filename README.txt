################################################################################
# This is the base configuration file for IHS AIX and Windows
#
# Author: eCommerce - OTech, OCIO
# Date: 01/01/2005
# Version: 1.0
#
# Description: This configuration contains the configuration for IHS
# 	and documents each function.
#
# Date: 03/03/2011
# Version: 1.5
#
#	Added IBM recommended SSl Configuration (IHS 2.0.47 or higher)
#	Passed OTech security scan 3/10/2011
#	Added monitoring for eCommerce group

# Version: 1.5.1
#
#	Added IBM recommended SSl Configuration (IHS 2.0.47 or higher)
#	http://www-01.ibm.com/support/docview.wss?uid=swg21112074
#	Changed d:\webDocs\htdocs to d:\webDocs

# Date: 07/12/2011
# Version: 2.0 Initial release/test
#
#	Added IBM recommended SSl Configuration
#	http://www-01.ibm.com/support/docview.wss?uid=swg21179559&acss=was131711
#
#	Added settings for password protected directories

# Date: 12/14/2011
# Version: 2.1 Add IBM recommendations and cleaned up 443 Virtual host config
#
#	Need to consider removing IPs from VM and replace with *:443
#	http://www-01.ibm.com/support/docview.wss?uid=swg21384688 (need to review this link to see if changes are needed)	
#
# Date: 6/6/2012
# Version: 2.1a Added support for password protected directories
#
# Date: 11/15/2012
# Version: 2.1b Added support for dynamic maintnace Page
#
# Date: 03/18/2014
# Version: 3.0 Merged Windows and AIX into one file.
# 	The master httpd.conf now uses include statements to activate different features and choose between Windows and AIX
#
# Date: 05/07/2014
# Version: 3.1 Fixed problems with merged configuration file were Windows does
#     not support the IBM diagnostic utilities, User and Group directive.
#     Changed the name of 14-Virtual-Host-SSL-Windows.httpd.conf
#
# Date: 11/01/2016
# Version:3.5 Several fixes, TLS 1.2 standardization 
#
# QUICK Start: Back up existing file before you begin.
#   1) Extract configuration from archive
#       Windows
#
#
#
#       AIX
#          httpd.conf_v3.5.tar into the /usr/HTTPServer directory on AIX
#          cd /usr/HTTPServer
#          tar -xvf <directory containing tar file>/httpd.conf_v3.5.tar
#   3) Verify these directories exist
#	Windows
#	   D:/HTTPServer (is the standard install directory)
#	   D:/HTTPServer/htdocs 
#		(this is for content to be served Fiilename:10-DocRootPerm-Windows.httpd.conf )
#	   D:/webLogs/HTTPServer
#       AIX
#          /usr/HTTPServer (is the standard install directory)
#	   /usr/HTTPServer/htdocs 
#		(this is for content to be served change as needed Filename:10-DocRootPerm-AIX.httpd.conf )
#	   /webLogs/HTTPServer
#   4) Verify the SSL keyfile
#	Windows
#	   D:\HTTPServer\keys\ihsserverkey.kdb exists
#       Aix
#          /usr/HTTPServer/keys/ihsserverkey.kdb exists if SSL being used
#   5) Verify the correct plugin information is locate on last 2 lines of httpd.conf.

# External resources:
#
# This is the main IBM HTTP server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://publib.boulder.ibm.com/httpserv/manual70/> for detailed 
# information about the directives.
#
# Do NOT enable features that are needed or without understanding
# what they do.  They are here as reminders of what is possible.  If you are unsure
# consult the online docs. 
#
# The configuration directives are grouped into three basic sections:
#  1. httpd.conf file is the master file that calls all the rest of the configurations.
#     It also includes the WAS plugin and sets its configuration
#  2. There are required Directives that must be included in every server installation.
#     These Directives are the Global directives and may be unique between Windows and
#     AIX, comment out the OS that is not being used and uncomment the OS that is being used.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. The optional Directives may be needed in some installations. Most can be included
#     without any impact to the servers performacne or security.
#  4. There are also sample configurations for Directives that are rarely used.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "logs/foo.log"
# On Windows with ServerRoot set to "D:/HTTPServer" will be interpreted by the
# server as "D:/HTTPServer/logs/foo.log".
# On AIX with ServerRoot set to "/usr/HTTPServer" will be interpreted by the
# server as "/usr/HTTPServer/logs/foo.log".
#
# Windows NOTE: Where filenames are specified, you must use forward slashes
# instead of backslashes (e.g., "c:/apache" instead of "c:\apache").
# If a drive letter is omitted, the drive on which Apache.exe is located
# will be used by default.  It is recommended that you always supply
# an explicit drive letter in absolute paths, however, to avoid
# confusion.
################################################################################
