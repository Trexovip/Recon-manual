UTR RECONCILIATION - HOSTING GUIDE
==================================

This folder has one file: index.html
Everything (including the Excel reader) is inside that file.
It needs no database, no PHP/Node/Python, and no internet connection
once it is on your server. Bank files are processed inside each user's
browser and are never sent to the server.

------------------------------------------------------------
OPTION 1 - cPanel / shared web hosting (GoDaddy, Hostinger, etc.)
------------------------------------------------------------
1. Log in to cPanel and open File Manager.
2. Go to public_html. Create a folder, e.g. "utr".
3. Upload index.html into that folder.
4. Open https://yourdomain.com/utr/

------------------------------------------------------------
OPTION 2 - Windows server (IIS), e.g. office intranet
------------------------------------------------------------
1. Copy index.html to C:\inetpub\wwwroot\utr\
2. Open http://SERVER-NAME/utr/ from any office PC.
   (If IIS is not installed: Server Manager > Add Roles >
    Web Server (IIS).)

------------------------------------------------------------
OPTION 3 - Linux server (Nginx or Apache)
------------------------------------------------------------
  sudo mkdir -p /var/www/html/utr
  sudo cp index.html /var/www/html/utr/
Open http://your-server-ip/utr/

Nginx example (own subdomain):
  server {
      listen 80;
      server_name utr.yourdomain.com;
      root /var/www/html/utr;
      index index.html;
  }
Add HTTPS for free with: sudo certbot --nginx

------------------------------------------------------------
OPTION 4 - Free hosting, no server needed
------------------------------------------------------------
Netlify: go to app.netlify.com/drop and drag this folder in.
         You get a link instantly; you can connect your domain later.
GitHub Pages / Cloudflare Pages: upload index.html to a repository
         and enable Pages.
Note: anyone with the link can open the page, but they cannot see
your data - files never leave the user's computer.

------------------------------------------------------------
OPTION 5 - No server at all
------------------------------------------------------------
Copy index.html to a shared drive and double-click it.
It opens in Chrome/Edge and works fully offline.

------------------------------------------------------------
RESTRICTING ACCESS (optional)
------------------------------------------------------------
To allow only your staff, put it on the office intranet, or add
password protection: cPanel > Directory Privacy, IIS > Basic
Authentication, or Nginx auth_basic.
