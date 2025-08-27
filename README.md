# Template for tiny Rails app with Telegram bot

Here you can find template for tiny Rails application with Telegram bot.
The repository itself is generated with this template.

What do you get:

- [telegram-bot](https://github.com/telegram-bot-rb/telegram-bot).
- RSpec for tests.
- Pry for debug.
- Simple bot controller.

This is just a template bot and it doesn't have much commands to show.
For more complex example see
[telegram_bot_app](https://github.com/telegram-bot-rb/telegram_bot_app).

For non-Rails app here is
[another example](https://github.com/telegram-bot-rb/telegram-bot/wiki/Non-rails-application).

## Setup

Here is a command to generate smallest possible installation of rails.
Choose yourself what railties to enable:

```
rails new app_name \
  --api \
  --skip-action-mailer \
  --skip-active-record \
  --skip-action-cable \
  --skip-test \
  -m https://raw.githubusercontent.com/telegram-bot-rb/rails_template/master/rails_template.rb
```

## After setup:

- Add this lines to `bin/setup`:
  ```ruby
  puts "\n== Copying sample files =="
  system 'bin/copy_samples'
  ```

- Setup bot config in `config/secrets.yml`.

- Uncomment these lines (based on rspec version) in `spec/rails_helper.rb`:
  ```ruby
  Dir[Rails.root.join('spec/support/**/*.rb')].each { |f| require f }
  ```
  Or

  ```ruby
  return unless Rails.env.test?

  Rails.root.glob('spec/support/**/*.rb').sort_by(&:to_s).each { |f| require f }
  ```

- _Optional._ Uncomment default configuration in `spec/spec_helper.rb`.

- _Optional._ If you don't use ActiveRecord,
  you may want to remove `config/database.yml` line from `bin/copy_samples`
  and `.gitignore`.

## Development

    bin/rails telegram:bot:poller

## Deployment

- Edit capistrano config.
- Make sure to add `config/secrets.yml` (and `config/database.yml` if exists)
  to shared folder on servers.
- See instructions in [wiki](https://github.com/telegram-bot-rb/telegram-bot/wiki/Deployment)

## License

MIT
