##Instructions on how to setup GeoMakers

####Update
```
sudo apt-get update
```


####Install Packages That We'll Use Later
```
sudo apt-get install -y curl vim git
```


####Install MySQL
```
sudo apt-get install -y mysql-server
sudo apt-get install mysql-client
sudo apt-get install -y libmysqlclient-dev
```


####Remove Old Ruby
Ubuntu sometimes ships with a messed-up version of ruby
```
sudo apt-get remove -y --purge ruby-rvm ruby
sudo rm -rf /usr/share/ruby-rvm /etc/rmvrc /etc/profile.d/rvm.sh
rm -rf ~/.rvm* ~/.gem/ ~/.bundle*
```


####Install Ruby Version Manager (RVM)
```
curl -L https://get.rvm.io | bash -s stable
```


####Install Ruby
```
curl -L https://get.rvm.io | bash -s stable --ruby=1.9.3
```

###Install Rails
```
gem install rails -v 3.2.18 --no-ri --no-rdoc
```


###Install Bundler
```
gem install bundler --no-ri --no-rdoc
```


###Download this Repository
We recommend placing it in the home directory
```
cd ~/
git clone http://github.com/DanielJDufour/geomakers.git
```


###Checkout respective branch
```
cd ~/geomakers
git checkout production
```


###Add user and password to database.yml
```
vim ~/geomakers/config/database.yml
```


###Install Gems
```
bundle update
bundle install
```


###Install Passenger
```
gem install passenger --no-ri --no-rdoc
```

###Setup Database
Create the tables, schema, and fill the database with example seed data:
```
rake db:setup
```
Move in the example data
```
rake db:migrate
```


###Step 14: Run the Rails app
```
rake test
passenger start
```
