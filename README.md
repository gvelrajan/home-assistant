<p align="center">
    <a href="https://socketxp.com" target="_blank"><img width="100"src="https://www.socketxp.com/wp-content/uploads/2019/06/socketxp-logo-darknavy.png"></a>
</p>

# Hass.io Add-on: SocketXP

Secure and fast reverse tunnels for your Home Assistant. 


<p align="center">
    <a href="https://www.socketxp.com/documentation" target="_blank"><img src="https://www.socketxp.com/wp-content/uploads/2020/04/SocketXP-Hassio.jpg"></a>
</p>

# About

SocketXP is a cloud based SaaS service that provides secure remote access to home automation services and IoT devices.  The SocketXP add-on  works by opening a secure reverse proxy connection to the public SocketXP Cloud Server and giving you your unique public URL with "socketxp.com" suffix,  You could share the SocketXP public URL to any 3rd party services.

SocketXP is very useful when:

* You cannot access your router to configure port forwarding
* You want to avoid the risk of opening up your router port to unwanted miscreants in the internet.
* Your Router doesn't support port forwarding
* Your ISP blocks inbound connections
* You don't have a static IP address
* Server that is hosting your home automation system is changing IP, location due to DHCP.

## Quick Start - TLS pass-through tunnel

Things to do before installing and starting the SocketXP add-on:

* Sign up [here](https://portal.socketxp.com)
* Get [DuckDNS](https://www.duckdns.org/) account and your personal domain name(optional, although recommended)
* Make sure your Home Assistant can terminate TLS with valid SSL Certificate and Key (You can get one from letsencrypt.org for free)

Installation of this add-on is simple, easy and straightforward:

  1. Add the SocketXP Hass.io add-ons Git repository URL to your Hass.io instance: https://github.com/socketxp-com/home-assistant (If you are seeing this through your Home Assistant add-ons page, skip it)
  2. Install the “SocketXP” add-on.
  3. Generate [auth token](https://portal.socketxp.com) and add it to the add-on's configuration.
  4. Create your own domain at [DuckDNS](https://www.duckdns.org/). Add the custom-domain details to the "tunnels" config section.
  6. Start the “SocketXP” add-on.  
  7. Check the logs of the "SocketXP” add-on to see if everything went well. It should print out your public URL.
  8. Use the SocketXP public URL to access your Home Assistant remotely or create a CNAME record in DuckDNS pointing your DuckDNS domain name to this public SocketXP URL 
  9. Now, use your DuckDNS.org domain URL to access your Home Assistant remotely.


## Plans and Pricing

SocketXP is a cloud based SaaS service hosted in Google Compute Platform.  Like any hosted service, SocketXP requires infrastructure, support and development time. Our business model is providing a service for a small fee. We do not share any of your data with 3rd parties (except with Stripe for billing purposes). We recommend the following two subscription plans:

* **Basic** plan that includes HTTPS and TLS tunnels - $4.99/month
* **Pro** plan that includes HTTPS, TLS tunnels + whitelabel domains - $9.99/month

## TLS pass-through tunnel config example

```json
{
    "authtoken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1ODgwNjI0MDIsImlkIjoiZ2FuZXNodmVscmFqYW5AZ21haWwuY29tIn0.Y2fv-OMYUXwp_yuSieuBb6v9XeA23492423488HERER",

    "tunnel_enabled": true,
    "tunnel" : {
		    "destination": "https://127.0.0.1:8123",
		    "protocol": "tls",			
		    "custom_domain": "your-name.duckdns.org"	
    },

    "relay_enabled": false, 
    "relay": {
        "destination": "https://127.0.0.1:8123"
    }
}
