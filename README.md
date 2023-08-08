## Steps to configure and setup vagrant for pushing a wordpress default website

1. Pick a ubuntu image greater than 20

    ```bash
    vagrant init jacobw/fedora35-arm64
    ```

2. Set the public and private network

3. Set the ram size needed for the server

4. Install the image and login to vagrant

   ``` bash
    vagrant up

    vagrant ssh
   ```

5. Switch to root user

   ```bash
   sudo -i
   ```

    (optional) - you can choose to change hostname (type 'i' for insert mode and then exit with :wq), then logout, login back and switch to root user.

    ```bash
    vim /etc/hostname {finance}

    hostname {finance}

    exit

    exit

    vagrant up

    sudo -i
    ```

6. install the following (-y flag is to automatically accept all)

    ```bash
    yum install unzip wget httpd vim -y
    ```

7. Start the httpd service

    ```bash
    systemctl start httpd
    ```

8. enable autostart from boot-time for httpd, stop and disable firewall service

    ```bash
    systemctl enable httpd

    systemctl stop firewalld

    systemctl disable firewalld
    ```

9. Check your default httpd page using the public IP of the server  (you can use the one from vagrant file) then write some markup in index.html (type 'i' for insert mode and then exit with :wq)

    ```bash
    cd /var/www/html

    vim index.html
    ```

    ```html
    <h1>Welcome Emmanuel!</h1>
    ```

    ```bash
    :wq
    ```

10. check your website, you can use the ip

    ```bash
    ip addr show
    ```

11. switch to temp folder, download and unzip the zipped website

    ```bash
    cd /tmp

    wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip

    unzip 2135_mini_finance.zip
    ```

12. copy the unzipped file to /var/www/html

    ```bash
    cd 2135_mini_finance

    cp -r * /var/www/html
    ```

13. Accept to auto-replace the previous index.html you created.

14. then check out the site

15. `exit` to leave root

16. power down vagrant to end

    ```bash
    vagrant halt
    ```
