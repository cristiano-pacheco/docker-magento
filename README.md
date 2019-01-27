# docker-magento
Docker for magento 2 based on https://github.com/markoshust/docker-magento

## Instalation

### Cloning

These commands will download the repository and prepare it for you.

```ssh
git clone https://github.com/cristianopacheco/docker-magento.git
cd docker-magento
rm -rf ./.git/
git init
git add --all
git commit -m "init"
```

### Download the magento source code

```ssh
bin/download 2.3.0
```

### Create the .composer directory and assign permissions to it

```ssh
sudo mkdir ~/.composer
sudo chmod -R 777 ~/.composer
```

### Create the entry in the hosts file with your custom domain

```ssh
echo "127.0.0.1 local.magento2.com" | sudo tee -a /etc/hosts
```

### Inform the authentication key of the magento marketplace in the project's auth.json file.

1. Log in to the magento market place (https://marketplace.magento.com/)
2. Go in the My Profile menu
3. Once logged in to Marketplace / My Products / Access Keys
4. Click the Create a New Access Key button
5. Rename the src/auth.json.sample file to auth.json
6. Inform key data in src/auth.json file

#### Remember that:
```ssh
username = Public Key
password = Private Key
```

### Creating the code directory

```ssh
mkdir src / app / code
```

### Starting containers
```ssh
bin / start
```

### Add the entry below in the file src/composer.json

```ssh
"replace": {
     "vertex / module-tax": "*"
}
```

### Change the bin/setup file with the data of your choice

### Start setup
```ssh
bin/setup
```

### You may now access your site!

```ssh
open https://local.magento2.com
```

## Sample Data Instalation (Optional)

### Install sample data
```ssh
bin/magento simple:data:deploy
```

### Upgrade the database
```ssh
bin/magento setup:upgrade
```

### Clean the cache
```ssh
bin/magento cacle:clean
```

## To enable Xdebug

```ssh
docker-compose down && docker-compose build
```
