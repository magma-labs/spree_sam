# SpreeSam
========

## Installation

Add spree_sam to your Gemfile:

```ruby
gem 'spree_sam', github: 'magma-labs/spree_sam'
```

Bundle your dependencies and run the installation generator:

```shell
bundle install
bundle exec rails g spree_sam:install
```

## Configuration

### Push notifications

Use `SpreeSam::Prefences` to configure push notifications provider and channels for specific events using a rails initializer in your app's config directory:

```ruby
# config/initializers/spree_sam.rb

SpreeSam::Preferences.configure do |config|
  config.notification_provider = "parse"
  config.notification_channels = {
    orders: {
      risky: ["providers", "customers", "administrators"]
    }
  }
end
```

#### Parse

You will need to setup your API key and app id through environment variables:

    PARSE_APP_ID
    PARSE_API_KEY

Also, if using channels, you can [specify them in a rails initializer](#push-notifications).


## Testing

First bundle your dependencies, then run `rake`. `rake` will default to building the dummy app if it does not exist, then it will run specs. The dummy app can be regenerated by using `rake test_app`.

```shell
bundle install
bundle exec rake
```

When testing your applications integration with this extension you may use it's factories.
Simply add this require statement to your spec_helper:

```ruby
require 'spree_sam/factories'
```

## License

[The new BSD licence](LICENSE) Copyright (c) 2015 Magma Labs.
