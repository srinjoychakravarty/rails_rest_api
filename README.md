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

# Create lean rails-api skeleton without database provisions:

$ rails new cow_say --api --skip-active-record

$ cd cow_say

# Remove pre-existing Gemfile.lock

$ sudo rm Gemfile.lock

# Add the following gems to gemfile after the gem 'puma':

gem 'ruby_cowsay'

gem 'jbuilder'

# Upgrade bundler

$ gem update --system

$ gem install bundler

$ bundler update --bundler

# Install all the gems from the updated gemfile

$ bundle install

# Update the /cow_say/config/routes.rb endpoint

    # config/routes.rb
    Rails.application.routes.draw do
      post 'say', to: 'cow#say'
    end

# Create a new controller in /cow_say/app/controllers

$ touch cow_controller.rb

# Update /cow_say/app/controllers/cow_controller.rb

    # app/controllers/cow_controller.rb
    class CowController < ApplicationController
      def say
        params.require(:message)
        params.permit(:cow, :balloon_type, :face_type)
        message      = params[:message]
        cow          = params[:cow] || 'cow'
        balloon_type = params[:balloon_type] || 'say'
       face_type    = params[:face_type] || 'default'
        @message = Cow
          .new(cow: cow, face_type: face_type)
          .say(message, balloon_type)
      end
    end

# Create a new view in /cow_say/app/views to serve json

    # app/views/cow/say.json.jbuilder
    json.message @message


# Start rails server on default port 3000

$ rails serve

# Test /say endpoint in a new terminal

$ curl localhost:3000/say -H 'Content-Type: application/json' -d '{"message": "Hello from RapidAPI", "cow": "sodomized", "balloon_type": "think"}' | ruby -r json -e "print JSON.parse(STDIN.read)['message']"

