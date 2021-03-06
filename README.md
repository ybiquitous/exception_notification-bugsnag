[![Gem Version](https://badge.fury.io/rb/exception_notification-bugsnag.svg)](http://badge.fury.io/rb/exception_notification-bugsnag)
[![Build Status](https://travis-ci.org/pocke/exception_notification-bugsnag.svg?branch=master)](https://travis-ci.org/pocke/exception_notification-bugsnag)

# ExceptionNotification::Bugsnag

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'exception_notification-bugsnag'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install exception_notification-bugsnag

## Usage

**NOTE: not use exception_notification's middleware.**

```ruby
ExceptionNotifier.add_notifier :bugsnag
# or
ExceptionNotifier.add_notifier :bugsnag, severity: 'error'
```

```ruby
begin
  # some code...
rescue => err
  ExceptionNotifier.notify_exception(err)
  # or
  ExceptionNotifier.notify_exception(err, severity: 'error')
  # or
  ExceptionNotifier.notify_exception(err) do |report|
    report.severity = 'error'
  end
```

### NOTE

- ignore `Bugsnag.configuration.auto_notify` (from 0.2.0)

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release` to create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

1. Fork it ( https://github.com/pocke/exception_notification-bugsnag/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
