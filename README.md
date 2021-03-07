# Practica11-IAW
## PASOS PREVIOS AL ESCANEO
Instalamos Docker si no lo tenemos: 
```
sudo apt install docker docker-compose
```

Cuando lo descarguemos tenemos que añadir al usuario en el grupo de usuarios de Docker, esto se hace mediante el comando: 
```
sudo usermod -aG docker $USER
```

Despues de esto habilitamos el servicio y lo arrancamos: 
```
sudo systemctl enable docker
sudo systemctl start docker
```
                                                         
Ahora tenemos que crear un contenedor para poner en funcionamiento el WPScan, para descargar la imagen usamos este comando:
```
docker pull wpscanteam/wpscan
```


## ESCANEO 1
Para obtener la lista de plugins instalados en nuestro sitio WordPress podemos ejecutar:

```
ubuntu@ip-172-31-69-249:~$ docker run -it --rm wpscanteam/wpscan --url http://3.235.181.10/ --enumerate p
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.15
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: http://3.235.181.10/ [3.235.181.10]
[+] Started: Sun Mar  7 10:19:22 2021

Interesting Finding(s):

[+] Headers
 | Interesting Entry: Server: Apache/2.4.41 (Ubuntu)
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: http://3.235.181.10/xmlrpc.php
 | Found By: Link Tag (Passive Detection)
 | Confidence: 100%
 | Confirmed By: Direct Access (Aggressive Detection), 100% confidence
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access

[+] WordPress readme found: http://3.235.181.10/readme.html
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] Upload directory has listing enabled: http://3.235.181.10/wp-content/uploads/
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] The external WP-Cron seems to be enabled: http://3.235.181.10/wp-cron.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 60%
 | References:
 |  - https://www.iplocation.net/defend-wordpress-from-ddos
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 5.6.2 identified (Latest, released on 2021-02-22).
 | Found By: Rss Generator (Passive Detection)
 |  - http://3.235.181.10/index.php/feed/, <generator>https://wordpress.org/?v=5.6.2</generator>
 |  - http://3.235.181.10/index.php/comments/feed/, <generator>https://wordpress.org/?v=5.6.2</generator>

[+] WordPress theme in use: vantage
 | Location: http://3.235.181.10/wp-content/themes/vantage/
 | Latest Version: 1.16.0 (up to date)
 | Last Updated: 2021-02-12T00:00:00.000Z
 | Readme: http://3.235.181.10/wp-content/themes/vantage/readme.txt
 | Style URL: http://3.235.181.10/wp-content/themes/vantage/style.css?ver=1.16.0
 | Style Name: Vantage
 | Style URI: https://siteorigin.com/theme/vantage/
 | Description: Vantage is a flexible multipurpose theme. Its strength lies in its tight integration with some power...
 | Author: SiteOrigin
 | Author URI: https://siteorigin.com/
 |
 | Found By: Css Style In Homepage (Passive Detection)
 |
 | Version: 1.16.0 (80% confidence)
 | Found By: Style (Passive Detection)
 |  - http://3.235.181.10/wp-content/themes/vantage/style.css?ver=1.16.0, Match: 'Version: 1.16.0'

[+] Enumerating Most Popular Plugins (via Passive Methods)
[+] Checking Plugin Versions (via Passive and Aggressive Methods)

[i] Plugin(s) Identified:

[+] bbpress
 | Location: http://3.235.181.10/wp-content/plugins/bbpress/
 | Latest Version: 2.6.6 (up to date)
 | Last Updated: 2020-11-06T01:28:00.000Z
 |
 | Found By: Urls In Homepage (Passive Detection)
 |
 | Version: 2.6.6 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - http://3.235.181.10/wp-content/plugins/bbpress/readme.txt

[+] cookie-law-info
 | Location: http://3.235.181.10/wp-content/plugins/cookie-law-info/
 | Latest Version: 2.0.0 (up to date)
 | Last Updated: 2021-02-18T10:33:00.000Z
 |
 | Found By: Urls In Homepage (Passive Detection)
 |
 | Version: 2.0.0 (100% confidence)
 | Found By: Query Parameter (Passive Detection)
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/css/cookie-law-info-public.css?ver=2.0.0
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/css/cookie-law-info-gdpr.css?ver=2.0.0
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/js/cookie-law-info-public.js?ver=2.0.0
 | Confirmed By:
 |  Readme - Stable Tag (Aggressive Detection)
 |   - http://3.235.181.10/wp-content/plugins/cookie-law-info/readme.txt
 |  Readme - ChangeLog Section (Aggressive Detection)
 |   - http://3.235.181.10/wp-content/plugins/cookie-law-info/readme.txt

[!] No WPScan API Token given, as a result vulnerability data has not been output.
[!] You can get a free API token with 25 daily requests by registering at https://wpscan.com/register

[+] Finished: Sun Mar  7 10:19:26 2021
[+] Requests Done: 35
[+] Cached Requests: 5
[+] Data Sent: 8.553 KB
[+] Data Received: 294.519 KB
[+] Memory used: 258.598 MB
[+] Elapsed time: 00:00:04
```


## ESCANEO 2
En este escaneo haremos uso de la API de WPScan que nos permite detectar vulnerabilidades haciendo uso de su base de datos de vulnerabilidades.
Para poder hacer uso del servicio de la API de WPScan es necesario registrarse en su web y obtener un TOKEN.

![](https://raw.githubusercontent.com/joseean29/Practica11-IAW/main/token.PNG)

```
ubuntu@ip-172-31-69-249:~$  docker run -it --rm wpscanteam/wpscan --url http://3.235.181.10/ --api-token 5ap4C4Tpjxa095mtxkyH9L5OGp2xTPzDKcbd5jf7Gmc
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.15
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: http://3.235.181.10/ [3.235.181.10]
[+] Started: Sun Mar  7 10:22:09 2021

Interesting Finding(s):

[+] Headers
 | Interesting Entry: Server: Apache/2.4.41 (Ubuntu)
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: http://3.235.181.10/xmlrpc.php
 | Found By: Link Tag (Passive Detection)
 | Confidence: 100%
 | Confirmed By: Direct Access (Aggressive Detection), 100% confidence
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access

[+] WordPress readme found: http://3.235.181.10/readme.html
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] Upload directory has listing enabled: http://3.235.181.10/wp-content/uploads/
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] The external WP-Cron seems to be enabled: http://3.235.181.10/wp-cron.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 60%
 | References:
 |  - https://www.iplocation.net/defend-wordpress-from-ddos
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 5.6.2 identified (Latest, released on 2021-02-22).
 | Found By: Rss Generator (Passive Detection)
 |  - http://3.235.181.10/index.php/feed/, <generator>https://wordpress.org/?v=5.6.2</generator>
 |  - http://3.235.181.10/index.php/comments/feed/, <generator>https://wordpress.org/?v=5.6.2</generator>

[+] WordPress theme in use: vantage
 | Location: http://3.235.181.10/wp-content/themes/vantage/
 | Latest Version: 1.16.0 (up to date)
 | Last Updated: 2021-02-12T00:00:00.000Z
 | Readme: http://3.235.181.10/wp-content/themes/vantage/readme.txt
 | Style URL: http://3.235.181.10/wp-content/themes/vantage/style.css?ver=1.16.0
 | Style Name: Vantage
 | Style URI: https://siteorigin.com/theme/vantage/
 | Description: Vantage is a flexible multipurpose theme. Its strength lies in its tight integration with some power...
 | Author: SiteOrigin
 | Author URI: https://siteorigin.com/
 |
 | Found By: Css Style In Homepage (Passive Detection)
 |
 | Version: 1.16.0 (80% confidence)
 | Found By: Style (Passive Detection)
 |  - http://3.235.181.10/wp-content/themes/vantage/style.css?ver=1.16.0, Match: 'Version: 1.16.0'

[+] Enumerating All Plugins (via Passive Methods)
[+] Checking Plugin Versions (via Passive and Aggressive Methods)

[i] Plugin(s) Identified:

[+] bbpress
 | Location: http://3.235.181.10/wp-content/plugins/bbpress/
 | Latest Version: 2.6.6 (up to date)
 | Last Updated: 2020-11-06T01:28:00.000Z
 |
 | Found By: Urls In Homepage (Passive Detection)
 |
 | Version: 2.6.6 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - http://3.235.181.10/wp-content/plugins/bbpress/readme.txt

[+] cookie-law-info
 | Location: http://3.235.181.10/wp-content/plugins/cookie-law-info/
 | Latest Version: 2.0.0 (up to date)
 | Last Updated: 2021-02-18T10:33:00.000Z
 |
 | Found By: Urls In Homepage (Passive Detection)
 |
 | Version: 2.0.0 (100% confidence)
 | Found By: Query Parameter (Passive Detection)
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/css/cookie-law-info-public.css?ver=2.0.0
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/css/cookie-law-info-gdpr.css?ver=2.0.0
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/js/cookie-law-info-public.js?ver=2.0.0
 | Confirmed By:
 |  Readme - Stable Tag (Aggressive Detection)
 |   - http://3.235.181.10/wp-content/plugins/cookie-law-info/readme.txt
 |  Readme - ChangeLog Section (Aggressive Detection)
 |   - http://3.235.181.10/wp-content/plugins/cookie-law-info/readme.txt

[+] Enumerating Config Backups (via Passive and Aggressive Methods)
 Checking Config Backups - Time: 00:00:00 <==============================================================> (22 / 22) 100.00% Time: 00:00:00

[i] No Config Backups Found.

[+] WPScan DB API OK
 | Plan: free
 | Requests Done (during the scan): 4
 | Requests Remaining: 21

[+] Finished: Sun Mar  7 10:22:13 2021
[+] Requests Done: 63
[+] Cached Requests: 5
[+] Data Sent: 15.386 KB
[+] Data Received: 309.341 KB
[+] Memory used: 217.754 MB
[+] Elapsed time: 00:00:03
```


## ESCANEO 3
Para realizar un escaneo completo de nuestro sitio WordPress ejecutaremos el siguiente comando:

```
ubuntu@ip-172-31-69-249:~$ docker run -it --rm wpscanteam/wpscan --url http://3.235.181.10/ 
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.15
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: http://3.235.181.10/ [3.235.181.10]
[+] Started: Sun Mar  7 10:24:15 2021

Interesting Finding(s):

[+] Headers
 | Interesting Entry: Server: Apache/2.4.41 (Ubuntu)
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: http://3.235.181.10/xmlrpc.php
 | Found By: Link Tag (Passive Detection)
 | Confidence: 100%
 | Confirmed By: Direct Access (Aggressive Detection), 100% confidence
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access

[+] WordPress readme found: http://3.235.181.10/readme.html
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] Upload directory has listing enabled: http://3.235.181.10/wp-content/uploads/
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%

[+] The external WP-Cron seems to be enabled: http://3.235.181.10/wp-cron.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 60%
 | References:
 |  - https://www.iplocation.net/defend-wordpress-from-ddos
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 5.6.2 identified (Latest, released on 2021-02-22).
 | Found By: Rss Generator (Passive Detection)
 |  - http://3.235.181.10/index.php/feed/, <generator>https://wordpress.org/?v=5.6.2</generator>
 |  - http://3.235.181.10/index.php/comments/feed/, <generator>https://wordpress.org/?v=5.6.2</generator>

[+] WordPress theme in use: vantage
 | Location: http://3.235.181.10/wp-content/themes/vantage/
 | Latest Version: 1.16.0 (up to date)
 | Last Updated: 2021-02-12T00:00:00.000Z
 | Readme: http://3.235.181.10/wp-content/themes/vantage/readme.txt
 | Style URL: http://3.235.181.10/wp-content/themes/vantage/style.css?ver=1.16.0
 | Style Name: Vantage
 | Style URI: https://siteorigin.com/theme/vantage/
 | Description: Vantage is a flexible multipurpose theme. Its strength lies in its tight integration with some power...
 | Author: SiteOrigin
 | Author URI: https://siteorigin.com/
 |
 | Found By: Css Style In Homepage (Passive Detection)
 |
 | Version: 1.16.0 (80% confidence)
 | Found By: Style (Passive Detection)
 |  - http://3.235.181.10/wp-content/themes/vantage/style.css?ver=1.16.0, Match: 'Version: 1.16.0'

[+] Enumerating All Plugins (via Passive Methods)
[+] Checking Plugin Versions (via Passive and Aggressive Methods)

[i] Plugin(s) Identified:

[+] bbpress
 | Location: http://3.235.181.10/wp-content/plugins/bbpress/
 | Latest Version: 2.6.6 (up to date)
 | Last Updated: 2020-11-06T01:28:00.000Z
 |
 | Found By: Urls In Homepage (Passive Detection)
 |
 | Version: 2.6.6 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - http://3.235.181.10/wp-content/plugins/bbpress/readme.txt

[+] cookie-law-info
 | Location: http://3.235.181.10/wp-content/plugins/cookie-law-info/
 | Latest Version: 2.0.0 (up to date)
 | Last Updated: 2021-02-18T10:33:00.000Z
 |
 | Found By: Urls In Homepage (Passive Detection)
 |
 | Version: 2.0.0 (100% confidence)
 | Found By: Query Parameter (Passive Detection)
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/css/cookie-law-info-public.css?ver=2.0.0
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/css/cookie-law-info-gdpr.css?ver=2.0.0
 |  - http://3.235.181.10/wp-content/plugins/cookie-law-info/public/js/cookie-law-info-public.js?ver=2.0.0
 | Confirmed By:
 |  Readme - Stable Tag (Aggressive Detection)
 |   - http://3.235.181.10/wp-content/plugins/cookie-law-info/readme.txt
 |  Readme - ChangeLog Section (Aggressive Detection)
 |   - http://3.235.181.10/wp-content/plugins/cookie-law-info/readme.txt

[+] Enumerating Config Backups (via Passive and Aggressive Methods)
 Checking Config Backups - Time: 00:00:00 <==============================================================> (22 / 22) 100.00% Time: 00:00:00

[i] No Config Backups Found.

[!] No WPScan API Token given, as a result vulnerability data has not been output.
[!] You can get a free API token with 25 daily requests by registering at https://wpscan.com/register

[+] Finished: Sun Mar  7 10:24:20 2021
[+] Requests Done: 57
[+] Cached Requests: 5
[+] Data Sent: 14.096 KB
[+] Data Received: 297.526 KB
[+] Memory used: 259.035 MB
[+] Elapsed time: 00:00:04
```
