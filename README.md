# Install rbenv:

$ cd

$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv

$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc

$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc

$ exec $SHELL

$ git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build

$ echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc

$ exec $SHELL

$ sudo apt-get install -y libssl-dev

# Install ruby 2.6:

$ rbenv install 2.6.0

$ rbenv global 2.6.0

$ ruby --version

$ rbenv rehash

# Install rails 2.6:

$ gem install rails -v 6.0.2.1

# Create lean rails api project without active record for database:

$ rails new cow_say --api --skip-active-record

# Remove pre-existing Gemfile.lock

$ sudo rm Gemfile.lock

# Upgrade bundler

$ gem update --system

$ gem install bundler

$ bundler update --bundler

$ bundle install

# Start rails server on default port 3000

$ rails serve
