# vagrant-digitalocean-docker-cookbook

Cookbook for setting up Docker on Digital Ocean using Vagrant and Chef.

## Supported Platforms

Tested using CentOS-6.5 on Digital Ocean.

## Requirement

- Vagrant
 - vagrant-digitalocean plugin
 - vagrant-omnibus plugin
- Chef (using knife-solo mainly)
- Berkshelf
- Digital Ocean
 - get Client ID and API Key
 - register SSH key

## Usage

```
git clone https://github.com/kun432/vagrant-digitalocean-docker.git
cd vagrant-digitalocean-docker
cp Vagrantfile.template Vagrantfile
vi Vagrantfile
berks vendor cookbooks
vagrant up --provider="digital_ocean"
```

I don't know why but, after your VM is booted, docker-CLI can't access docker-daemon. You must restart docker-daemon once.

```
vagrant ssh
service docker restart
```

## Vagrantfile

Edit following param for your environment:

```
provider.client_id            = 'YOUR_CLIENT_ID'
provider.api_key              = 'YOUR_API_KEY'
provider.ssh_key_name         = 'YOUR_SSH_KEY_NAME'
override.ssh.private_key_path = 'YOUR_SSH_KEY_PATH'
```

```
provider.image                = 'CentOS 6.5 x64'
provider.region               = 'Singapore 1'
provider.size                 = '512MB'
```


## Contributing

1. Fork the repository on Github
2. Create a named feature branch (i.e. `add-new-recipe`)
3. Write your change
4. Write tests for your change (if applicable)
5. Run the tests, ensuring they all pass
6. Submit a Pull Request

## License and Authors

Author:: Kuniaki Shimizu (<k.shimizu@8d1w.com>)
