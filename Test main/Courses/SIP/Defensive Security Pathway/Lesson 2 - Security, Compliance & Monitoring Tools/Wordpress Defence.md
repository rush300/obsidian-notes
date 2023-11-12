# Introduction

If you’re taking a stock WordPress install and hardening it, consider adopting these early on in the engagement and set the expectations with the site owners regarding good security hygiene.

The key takeaways for the bare minimum are:

- Security by least privilege - don’t give more privs than needed!
- Account separation - don’t let people share an account
- MFA
- Attack surface reduction

  

# Remove the Default Admin User

When WordPress is first installed there’s a default user account created, generally named _admin_, that’s used to login to the CMS and configure the site. However, many people who install WordPress regard the admin account as “the account” and use it for everything, and they share it out to people they want to update the site - bad practice!

As soon as WordPress is installed, create a new admin account for you to login with. Once you’ve done that, delete the default account.

![84d0f4_52f6c553a0ef404eb3702d4adb169e4a-mv2.png Thumbnail](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.fs.teachablecdn.com/s5YIxv6NSe6z9psNTTvM)

_Big Brain Play: Consider making the accounts for staff who are going to be managing the content first, and create your admin account at the end. There’s an assumption that the earlier user IDs are typically the admin accounts, so this will throw off someone brute-forcing login attempts on users with the lower ID numbers!_﻿

# Use an Editor Account for Publishing Posts

As we just talked about, many people who install WordPress just share the one account for everything to do with the site - posts, maintenance, the lot! This is a bad way to go for many reasons, and as WordPress posts show the author on blog posts by default, that leaves the username in plain sight for anyone doing recon. This can be fixed by assigning the Editor role to those who are posting content to the site.

The Administrator role isn’t required to publish new content to a WordPress site, so it makes perfect sense to set the appropriate role for what those users are going to be doing on the site. If posting content is being delegated to the site admin, then that person should have two user accounts in the WordPress instance; one account is used for posting new content, and the other is for site administration.

Even though it’s the same human doing those tasks, having a separate admin account that’s not used for posting content will help to keep that account footprint as small as possible.

# Require MFA for Admins and Editors

Pretty straightforward - admins control the site as a whole and editors control the content, so it makes sense to keep those accounts secured with an MFA solution. The most straightforward implementations are through a site plugin that injects the 2FA prompt into the login page, most notably **Google Authenticator**, **Wordfence**, and **Duo Two-Factor Authentication**. All of these plugins enable 2FA and you can opt to require opt-in based on the site role.

  

Want to take things a step further? If the site owners are using an existing Single Sign-On solution elsewhere in their business, you can use a SAML plugin to hook into the pre-existing login requirements that the business already has in place. This is fantastic if there are already MFA requirements implemented, as this will be one less step for those users to deal with. Once they login via the SSO page, they get sent back to the WordPress site with an authenticated session.

# Backup and Patch Regularly

Updates to WordPress core, plugins and themes provide new functionality, feature improvements, and security patches that make exploiting the site more difficult. Because of this, it’s important to keep WordPress updated, along with third-party plugins and themes.  

Before updating, however, it is also important to make a full backup of the site in case an update introduces a problem with the website. Backups can be done a number of ways; however, the easiest method is with a plug-in like BackupBuddy, VaultPress or Duplicator. Duplicator has a free tier that allows for manually creating a self-contained backup of the website and the database, whereas BackupBuddy and VaultPress have paid tiers that allow for automations and greater flexibility.

# Use Sound Judgement Around Plugins and Themes

It’s generally accepted that too many plugins and themes can slow down a WordPress install; however, the greater concern is that the site is vulnerable to attack if some plugins or themes aren’t updated. This is typically seen with child themes based on an old version of another theme (often no longer supported). Remove any plugins and themes that are not in use on the site to reduce the available attack surface (and maybe claw back some performance).  

Be wary of the free plugins and themes on the marketplace as well. There’s a treasure trove of free plugins and themes created for WordPress, but free needs to be balanced against the risk of malicious code, encrypted links, viruses and backdoors.  

When it comes to trustworthy sources, the WordPress.org plug-in and theme repositories are the safest place to find free plugins and themes. Most plug-in and theme creators (Divi, Elementor, Oxygen etc.) and marketplaces like Envato are also safe. However, if someone has made a premium/paid theme available for free, this is potentially dangerous. Perform due diligence and exercise caution when adding new plugins to the site.  

> Tip: Install the [WPScan](https://wordpress.org/plugins/wpscan/) plugin on the site and supply an API token, and this will regularly scan the site’s plugins and themes for vulns - just like the CLI tool we know and love!

  

# Hard Mode The Easy Way

These countermeasures contain a mix of plugin recommendations and direct configuration file edits, as well as a database change or two. These have a greater chance of breaking some WordPress features if not implemented correctly, especially if you edit the WordPress Core (there’s no reason to), or if other users are going to be involved in ongoing design and development (as the config will no longer be the standard they expect).

# Limit Login Attempts

WordPress has no brute-force attack countermeasures out of the box; that is to say that you can try usernames and passwords as much as you like until you get it right. There are plugins such as Loginizer and Login LockDown that can restrict the number of times a user can attempt to login before getting locked out. You can also use these plugins to block IP ranges, disable login error messages, and prevent threat actors from entering invalid usernames.  

> Think of this as fail2ban just for WordPress - if you have access to the underlying server and can install packages, fail2ban would be a better solution. If you don’t have that, then implementing it here is the next best thing.

  

# Rename the WordPress Login Page

WordPress installs by default map the admin logon form at the /wp-login.php URI. There is a small advantage to renaming this login page, as it can fool simpler bots and site crawlers looking for the login form to brute-force later.  

To rename the login page, install and activate the WordPress Hide Login plugin and change the login URL to suit.

# Change the WordPress Database Prefix

Standard WordPress installs apply a prefix to each of the table names in the database, the default prefix being _wp__. There’s a small advantage to changing this prefix to something different; this can help prevent attacks against the database, as an attacker would need to guess the correct table prefix in order to carry out the exploit. This is ideally a change to make during the WordPress installation, but it can be done on an existing site.  

To change the table prefix:Change the $table_prefixvalue in the site’s wp-config.php file from _‘wp_’_ to something else, ideally something not easily guessed.  

Login to MySQL via the terminal (or open phpMyAdmin) and rename each table in the database with the _wp__ prefix:

![Screenshot 2022-08-02 195359.png Thumbnail](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.fs.teachablecdn.com/kEBYIzRjbJgBoMXCrAso)

Update the _usermeta_ table:

![Screenshot 2022-08-02 195543.png Thumbnail](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.fs.teachablecdn.com/CANGohSYSyK5BQtPNw0i)

Update the _options_ table:

![Screenshot 2022-08-02 195939.png Thumbnail](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.fs.teachablecdn.com/OA1cxvTRZG61fyk4RUpS)

This can also be accomplished via plug-ins like iThemes Security. There is another plug-in on the WordPress plug-in directory called Change Table Prefix that accomplishes the same task.﻿

# HTACCESS POWER ROUND

The .htaccess file is used for URL redirections, rewriting URLs, configuring permalinks, and a host of other functions. When used effectively, it can also provide some security hardening. A site can have multiple .htaccess files if required. Each site may have its own unique requirements when using .htaccess files, so here are some example configurations.

  
If you have access to the underpinning Apache or Nginx server on the host, you can handle many of these options in either the main config file or by including files for specific virtual hosts. Check out the HTTP Defender module for a deeper look into securing Apache and Nginx server binaries.

  
For now, let’s get into what we can do with .htaccess files!

# Disable Directory Browsing

To disable directory browsing, add the following line to the end of the .htaccess file in the root of the WordPress directory:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/eGUzWkqbR3o9nVZwyL86)

# Disable PHP Execution

If site visitors need to be able to upload files to the site as part of their interactions, you will need to make some of the WordPress site directories writable in order to achieve this. This is enabled out of the box, but there are no protections in place in the event that someone uploads a malicious script to the site and then runs it.This can be easily fixed with a.htaccess file in /wp-content/uploads/. Save the code snippet below into a file named .htaccess and upload it to the uploads directory.

  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/lekwkHKTB2dmJ2BhYjqv)

# Protect the WordPress Config File

One of the most crucial files for any WordPress install is the wp-config.php file in the root of the site. This file contains information such as the credentials to the site’s database, WordPress salts and other settings required for the site to function. There is no reason for a site visitor to be able to get access to this file, so it can be blocked in the .htaccess file in the site root. Add this snippet to the end of the file:

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/XyMA2GpQqiJHCmEXm5dS)

# Protect the Root .htaccess File

Much like the wp-config.php file, restrict the .htaccess file by adding this snippet to the end of the .htaccess file in the site root:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/8mGPMvTUC22wK2EbEVWw)

  

Pro tip: If you want to protect wp-config.php, .htaccess, php.ini and error_log files in one snippet, use this snippet in place of the two above.

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/mxhhtDUR92Q43D9qjc7A)

# Block All Access to WordPress Includes

The /wp-includes/ folder contains all of the core WordPress files. There is no reason for anyone to have access to this folder over the web, including site owners and admins – so it’s a good idea to restrict access to it. Add this to the end of the .htaccess file in the site root:

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/NY74gTERTUacrPquyN95)

# Protect the WordPress Content Directory

To protect the /wp-content/ folder from unauthorized access, create a separate .htaccess file in the /wp-content/ directory on the site and add this snippet to it:  

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/tOFZ3zwTpmJnVkqC7xWF)

The code snippet below will protect the site against common XSS attacks, namely script injections and attempts to modify global and request variables. If you know that XSS is required by the site then you will want to leave this disabled; otherwise, add the snippet into the .htaccess file in the site root.

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/HYPqYCbMTNu3sCfFAKoM)

# Sane File and Directory Permissions

This assumes you as the defender have root SSH access to the host and can run commands in a terminal directly, and that the owner and group are already set correctly.

  
To set the permissions for WordPress files and folders, login to an SSH session on the web server, change into the WordPress directory and then execute the following commands(enter your password when prompted):

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/S23ybva8TpO0fB7ip71J)  

This will recursively set the correct permissions for files and directories in the WordPress site directory, and then lock down the wp-config.php file so that only the file owner has access.

# Custom Countermeasures

So far we’ve taken some of the more basic steps in hardening a WordPress installation. Now it’s time to start making changes to the WordPress configuration to make things even harder for recon efforts and subsequent attacks.

  
For countermeasures that require editing the active theme’s functions.php file, the site developer should consider creating the main theme to function as a parent theme, and then create a child theme to handle the countermeasures. The parent-child theme relationship ensures that the child theme inherits all of the parent theme’s functionality, which means that the dev can update the parent theme without overwriting the child theme’s countermeasures.

# Move the Config File

The wp-config.php file is normally found in the site’s root directory on the hosting server (e.g. /home/user/public_html/ or /var/www/html/ for a VPS), but can safely be moved one directory up without breaking the site. WordPress will automatically look one directory above for the file.

# Update WordPress Security Keys

The wp-config.php file contains security keys that handle the salting and encryption of information stored in the cookies downloaded by site users. These should be randomly generated for each WordPress installation and can be done using the [WordPress Salts Key Generator](https://api.wordpress.org/secret-key/1.1/salt/). If the site’s chosen security plug-in has a function to change the WordPress Salts, this can also be used.

# Disable Error Reporting

If plug-ins or themes cause errors, the error message may display the server path, which can be used and abused. It’s better to disable error reporting on production sites altogether by adding the following code to wp-config.php:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/RRJ9MqeQ3iIzRo8nm3Hg)

# Disable Error Reporting for the Theme

If the site is using a custom theme or child theme, add this line to the theme’s functions.php file to disable error reporting:

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/9iFFTHoOSHpL0yZSkZpA)

# Disable Plugin and Theme Editors

Unless developers need to make changes to themes and plugins on the fly, there’s no reason to have the plugin and theme editors enabled on the site. Disable them by adding the following code to wp-config.php:

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/yKxuke8RW6wwQ7Nxo9og)

# Remove the WordPress Version Number

WordPress places a meta tag in the website’s HTML that states the version of WordPress powering the site. This is useful in an exploit because knowing the WordPress version makes it easier to find vulnerabilities to use. Add this to the active theme’s functions.php file to stop the tag being added:  

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/7h9qFXogQdWWkX5nE1xF)

# Disable WordPress Login Hints

By default, when you login to WordPress and type in an incorrect or non-existent username, or a bad password, WordPress gives a detailed message indicating which of the two is wrong – either the username doesn’t exist or the password doesn’t match. This is very bad from a security perspective as this can be used to find out what valid user accounts are set up in the site.

  
Add this code snippet into the active theme’s functions.php file to change the login error message to something different:

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/8pC0QFjLSCGIJsxIx4c9)

# HTTP Header Security

HTTP security headers help mitigate attacks and security vulnerabilities by specifying what types of scripts, resources, images and styles can be loaded onto the site. There are six HTTP security headers that you can add into WordPress by adding them in the theme’s functions.php file.

  
You can add the headers manually, or use a plugin like Security Headers to load it for you. Either way, once the headers are loaded in, be sure to test them out by going to [https://securityheaders.com/and](https://securityheaders.com/and) scanning the site. Like the custom countermeasures, if you choose to add the headers to the theme’s functions.php file, consider using a child theme to handle it.

# X-Frame-Options

This header helps prevent clickjacking attacks by telling the browser that it shouldn’t render the page in a frame (or iframe or object). Add this into the theme’s functions.php file:

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/WESHisUTpipQuP3hHsEa)

# Content Security Policy (CSP)

CSP helps mitigate XSS attacks by whitelisting the allowed sources of content like scripts, styles and images. In short, a CSP can prevent the browser from loading potentially malicious assets on the site from places it shouldn’t be loading them from.

  
There’s no one-size-fits-all approach to CSPs, so you will need to evaluate the resources you’re actually loading on the site. Once you have an idea of what’s being loaded in, you can start making a policy based on those requirements.

  
Here’s an example CSP header added into the theme’s functions.php file (on one line):  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/ogI6qscDTduZ2VDIy9tq)  

The CSP header above allows all resources from the current domain (‘self’). The unsafe-inline option tells the browser that in-line styles and script tags are allowed, and unsafe-eval tells the browser that unsafe dynamic code evaluation such as JavaScript is allowed. The https: and data: options tell the browser that it can only load resources over HTTPS and data schemes.

# X-XSS-Protection and X-Content-Type-Options

These headers also help mitigate XSS attacks. In particular, the X-Content-Type-Options header tells Internet Explorer not to sniff MIME types, preventing MIME-sniffing attacks. Add them into the theme’s functions.php file:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/YdCc2zVCSWerbR6ty748)

We know that Internet Explorer should die in a fire, but there are still the die hards that will not change to anything other than what they’re used to. MIME-sniffing countermeasures are for them.

  
Modern browsers have dropped XSS filters or chosen not to implement the X-XSS-Protection header due to potential reflected XSS, as discussed [here](https://chromestatus.com/feature/5021976655560704) and [here](https://bugzilla.mozilla.org/show_bug.cgi?id=528661). This is therefore most useful as a countermeasure for IE.

# HTTP Strict Transport Security (HSTS)

HSTS is a method for the web server to instruct the browser to only communicate with the server over HTTPS. Add it to the theme’s functions.php file:

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/1xWkGWUYTfOHDoMZCnF9)

# Implement Cookie with HTTPOnly and Secure Flag

This tells the browser to only trust cookies from the server and make sure they are only accessible over SSL. Add it to the theme’s functions.php file:

﻿![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/TbH5r7TkRwqH34Dfhs57)

# Adding Google Search Console (GSC)

Aside from its usefulness regarding SEO and how Google understands the website, GSC has a dashboard dedicated to security issues. If Google detects an issue with the site and has determined its compromised, you will get an email alert advising as such.

# Advanced SSL Implementations

SSL is the cryptographic tech underpinning encrypted connections between web servers and visitors’ browsers. Having SSL enabled on the site is critical now, as not only is it needed for e-commerce sites, but it can play a role in your site’s search engine rankings. Most shared hosting providers have an option in cPanel to generate a free SSL certificate using either LetsEncrypt or AutoSSL, and is easy to link to the domain.

Those using a VPS often don’t have such tools, but there are plenty of guides on how to install the LetsEncrypt tools to get a free SSL certificate. Once the certificate is installed, install a plugin such as Really Simple SSL to force the site to redirect any non-SSL requests to SSL.

There are other solutions to implementing and automating SSL, such as certificate pinning with a service such as Cloudflare and applying an origin cert to the host, and in more advanced deployments, making use of a load balancer or reverse proxy and having it terminate the SSL endpoint there. The latter is geared more towards sites deployed on a Kubernetes cluster or other container infrastructure.

# Extra Credit: Trellis WordPress Deployment

This is not for the faint of heart, is a non-standard WordPress deployment and thus not what you will normally encounter, but this is a more controlled way of deploying WordPress for both the developer and for a maintainer. Instead of the spray-and-pray approach to applying core, plugin or theme updates, Trellis uses git to clone the current codebase and then applies the updates on the site clone. If the updates don’t work, roll back to the previous clone with zero downtime.

  
Read more on Trellis at [https://roots.io/trellis/](https://roots.io/trellis/).

## Lesson Summary

This text provides a summary of important security measures that can be implemented on a WordPress website:

- Add custom security headers, such as X-Frame-Options, Content Security Policy, X-XSS-Protection, X-Content-Type-Options, and HTTP Strict Transport Security.
- Implement SSL certificates and secure cookies with HTTPOnly and Secure flags.
- Use Google Search Console for monitoring security issues.
- Consider advanced SSL implementation methods, such as using Cloudflare or a load balancer.
- Utilize Trellis WordPress Deployment as a controlled method for deploying WordPress updates.
- Possibly implement a web application firewall.
- Secure WordPress hosts using containerized workloads and access control measures.

The text provides a guide on how to harden a WordPress installation for improved security, with the following key recommendations:

1. Remove the default admin user and create a new admin account.
2. Use an editor account for publishing posts instead of sharing one account for all tasks.
3. Implement multi-factor authentication (MFA) for admins and editors.
4. Regularly backup and patch WordPress core, plugins, and themes.
5. Be selective with plugins and themes, remove unused ones and be cautious of free options.
6. Limit login attempts and rename the WordPress login page.
7. Change the WordPress database prefix to prevent database attacks.
8. Use .htaccess files to disable directory browsing and PHP execution, protect important files, and block access to certain folders.
9. Set correct file and directory permissions.
10. Move the wp-config.php file one directory up and update WordPress security keys.
11. Disable error reporting, plugin and theme editors, and remove the WordPress version number from the website's HTML.
12. Change the WordPress login error message and add HTTP security headers.

These measures aim to enhance the security of a WordPress site and reduce the risk of attacks and vulnerabilities.

# Wrap Up

Congratulations! You’ve made it to the end of the module, which means you now have a solid base to build your WordPress defence on.

  
There are obviously more strategies you can take, such as implementing a web application firewall directly into WordPress, or you can use another external service to provide that functionality. Access to the WordPress host itself can be further secured by using containerised workloads and deploying an access control plane such as Teleport to manage access to the underlying hosts and enforce MFA on those logins. The possibilities truly are endless here!