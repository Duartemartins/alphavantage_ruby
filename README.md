# Alpha Vantage Ruby Library

The Alpha Vantage Ruby library provides convenient access to the [Alpha Vantage API](https://www.alphavantage.co/documentation/) from applications written in the Ruby language.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'alphavantage'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install alphavantage

## Usage

The library needs to be configured with your account's api key which you can obtain from https://www.alphavantage.co/support/#api-key.
Set the `Alphavantage.configuration.api_key` to its value. If you are using Rails, you can configure this in an initializer.

```
require 'alphavantage'

Alphavantage.configure do |config|
  config.api_key = 'your-api-key'
end
```
### Accessing Stock Time Series

```
Alphavantage::TimeSeries.search(keywords: 'Tesla')
stock_timeseries = Alphavantage::TimeSeries.new(symbol: 'TSLA')
stock_timeseries.quote
stock_timeseries.monthly
stock_timeseries.monthly(adjusted: true)
stock_timeseries.weekly
stock_timeseries.weekly(adjusted: true)
stock_timeseries.daily(outputsize: 'compact')
stock_timeseries.daily(adjusted: true, outputsize: 'full')
stock_timeseries.intraday(adjusted: true, outputsize: 'compact', interval: '5min')
```
### Accessing Fundamental Data
```
company = Alphavantage::Fundamental.new(symbol: 'TSLA')
company.overview
company.earnings
company.income_statement
company.balance_sheet
company.cash_flow
```
### Accessing Forex
```
forex = Alphavantage::Forex.new(from_symbol: 'USD', to_symbol: 'JPY')
forex.exchange_rates
forex.intraday(interval: '5min', outputsize: 'compact')
forex.daily(outputsize: 'compact')
forex.weekly
forex.monthly
```
## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/codespore/alphavantage_ruby. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Alphavantage project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/codespore/alphavantage_ruby/blob/master/CODE_OF_CONDUCT.md).
