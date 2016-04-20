How To Create a SSL Certificate on Nginx for Ubuntu 14.04
==========================================================

Prerequisites
-------------

You are also going to need to have Apache installed:

.. code-block:: console
    
    $ sudo apt-get update
    $ sudo apt-get install nginx

1. Create a SSL Certificate
---------------------------------------

Create location where contains certificate files:

.. code-block:: console

   $ sudo mkdir /etc/nginx/ssl

Create the key and cerfiticate:

.. code-block:: console

    $ sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/ssl/nginx.key -out /etc/nginx/ssl/nginx.crt

More detail:

* **openssl**: cli tool which is provided by OpenSSl to create and manage key, cerfiticate, signing requests ...
* **req**: specifies a subcommand for X.509 certificate signing request (CSR) management. More detail for X.509 `here <https://en.wikipedia.org/wiki/X.509>`_.
* **-x509**:  specifies that we want to make a self-signed certificate file instead of generating a certificate request.
* **-nodes**: don't use passphrase for key file.
* **-day**: the number of days that key and cerfiticate are valid.
* **-newkey**: create the cerfiticate request and a new private key at the same time.
* **rsa:2048**: rsa key and 2048 bits.
* **-keyout**: output file where contain private key.
* **-out**: output file where contains cerfiticate.

2. Configure nginx to use SSL
------------------------------

Create your nginx configuration file:

.. code-block:: console

    $vim /etc/nginx/conf.d/ssl_nginx.conf


and add to above file:

.. code-block:: ini

    server {
            listen 80;
            listen 443 ssl;
    
            root /usr/share/nginx/html;
            index index.html index.htm;
    
            ssl_certificate /etc/nginx/ssl/nginx.crt;
            ssl_certificate_key /etc/nginx/ssl/nginx.key;
    
            location / {
                    try_files $uri $uri/ =404;
            }
    }

Then, restart nginx service for loading the changes:

.. code-block:: console

    $ sudo service nginx restart


3. Verification
---------------

Visit your server's domain name or IP with `https` protocol::

    https://server_domain_name_or_IP 


For more detail, please refer to `here <https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04>`_.
