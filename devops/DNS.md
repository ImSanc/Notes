#### What is DNS?
 - DNS (Domain Name System) is like a phonebook for the internet. It translates human-readable domain names (e.g., imsanc.com) into IP addresses that computers use to communicate.


##### Example of my Cloudflare DNS

Your DNS Records
Your DNS settings in Cloudflare include different types of records:

Type	    Name	            Content	                    Proxy Status	 TTL	Purpose
A	       imsanc.com	      IP addreesss              	Proxied	        Auto	Points imsanc.com to an IP address (hosting provider).
CNAME	_domainconnect	    _domainconnect.gd...	        Proxied	        Auto	Used for domain connection (automatically generated).
CNAME	    www	                imsanc.com	                Proxied	        Auto	Redirects www.imsanc.com to imsanc.com.
Worker	medium.imsanc.com	    backend	                    Proxied	        Auto	Routes medium.imsanc.com to a Cloudflare Worker.


#### Types of DNS records 
 - A Record (Address Record)

    Points a domain/subdomain to an IPv4 address.
    Example: imsanc.com → 13.248.243.5.

   - CNAME Record (Canonical Name)
    Maps a domain to another domain instead of an IP.
    Example: www.imsanc.com → imsanc.com.

   - Worker (Custom Cloudflare Route)
    Used to route traffic through Cloudflare Workers.
    Example: medium.imsanc.com is mapped to the backend worker.


#### What is Proxy Status?
 - Proxied (Orange Cloud ☁️) → Traffic goes through Cloudflare (hides origin IP, adds security, and optimizes speed).
 - DNS Only (Grey Cloud ☁️) → Traffic goes directly to the destination without Cloudflare protection.

You have Proxied enabled, meaning Cloudflare is caching, securing, and optimizing your website traffic.

#### 5. What is TTL (Time to Live)?
 - TTL defines how long a DNS record is cached before checking for updates.

 - Auto TTL (Default in Cloudflare) → Cloudflare automatically manages it for better performance.
 - Custom TTL (e.g., 300 seconds) → Tells DNS resolvers to check for updates every 5 minutes.


#### 7. How to Add a Subdomain (Like api.imsanc.com)
If you want to add a subdomain (api.imsanc.com) pointing to your Cloudflare Worker, follow these steps:

 - Go to Cloudflare Dashboard → DNS.
 - Click "Add record".
 - Choose Type: Worker.
 - Name: api.imsanc.com
 - Target: backend (or the correct Worker name).
 - Ensure Proxy Status is Proxied.
 - Click Save.