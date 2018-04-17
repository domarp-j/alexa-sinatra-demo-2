# Alexa Sinatra Demo Continued - Pizza Buddy

This is Part 2 of the demo for setting up an Alexa skill with Ruby! Go through the [AWS custom skills documentation](https://developer.amazon.com/docs/custom-skills/understanding-custom-skills.html) to see the full depth of Alexa's capabilities.

Based on a great guide by Maker's Academy: https://developer.amazon.com/alexa-skills-kit/makers-academy

This is a continuation of the [first part of this demo](https://github.com/domarp-j/alexa-number-facts) which goes through the basics of creating a dialogue model and setting up a Sinatra app for handling Alexa requests. If you haven't seen it already, check that out first!

A skill called "Pizza Buddy" is created as part of this demo, using (in addition to Sinatra and ngrok):
- [ralyxa](https://github.com/sjmog/ralyxa), a gem that easily handles Alexa requests & responses
- [data_mapper](https://github.com/datamapper/data_mapper) and Postgresql for persistence

## Setup

### Part 1 - Using Ralyxa

1. In your `server.rb` file, make sure that you `require 'ralyxa`
2. Create a single `post` action like so:
```
post '/' do
  Ralyxa::Skill.handle(request)
end
```
3. Create a new `intents/` directory
4. For each intent that you have defined in the AWS Alexa Developer Console, create an intent `.rb` folder with the following format:
```
intent 'IntentName' do
  # See the documentation of Ralyxa for what you can do here!
end
```

### Part 2 - Using Data Mapper & Postgresql

1. Install the `data_mapper` and `dm-postgres-adapter` gems
2. Create a Postgresql database locally
3. Create a `database.rb` file in the same format as the `database.rb` file in this repo
4. Load `database.rb` in `server.rb`
5. For any classes that you would like to reflect as models, make sure to `include DataMapper::Resource` and define properties as needed (see `lib/pizza`). They will behave a lot like Rails models.

