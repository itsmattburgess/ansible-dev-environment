# Local development environment services
This repository uses ansible to configure my local development environment to the following specifications:
- Apache 2.4
- PHP 7.0
- MariaDB
- Redis
- RabbitMQ
- Other utilities (freetds, composer, supervisor etc)

## Running ansible
Run the following command to get ansible working away: ```ansible-playbook playbook.yml -i hosts --ask-become-pass```

## Apache configuration
I have configured Apache to run a VirtualDocumentRoot virtual host. To host a new site you should place the site directory (or symlink to the public directory) in your ``~/Sites/`` directory. Dnsmasq is installed and configured to catch all ```*.dev``` domains and pass the requests to the local Apache server using the name of your directory.

For example, if you have a directory called ``~/Sites/test-site``. This site will be accessible through ```http://test-site.dev``` without the need to change any apache config.

Apache is setup to accept HTTP and HTTPS requests.

I would suggest following my directory structure, where all directories inside ```~/Sites``` are a symlink to the public directory of the repository somewhere else on my filesystem, i.e. ```~/Github/itsmattburgess/test-site``` for maximum flexibility.
