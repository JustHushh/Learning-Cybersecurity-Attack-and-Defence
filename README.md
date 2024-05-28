# Learning-Cybersecurity-Attack-and-Defence
Testing the resistance of cybersecurity attacks of a travel agency website, and demonstration on two versions of website, protected and unprotected.

To use our project you need to install: OpenServer
1) Main.no - unprotected version of the project
2) Main.security - protected version of the project

Just install two version of website, place it in the projects folder and configure data base.

1)areaweb - name of the DB to unsecured(Main.no) project
2)areaweb2 - name of the DB to secured(Main.security) project

If you want to change the name of the DB, you can you can go to config files(src/config.php) and and change it in DB_NAME const, and you should note that if DB name is changed in code it also should match in phpMyadmin DB name.
