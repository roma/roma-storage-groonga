# roma-storage-groonga

A [Groonga](https://groonga.org/) storage for [ROMA](https://github.com/roma/roma), a distributed key-value store.

## Installation

This gem uses [rroonga](https://github.com/ranguba/rroonga), which needs Groonga 12.0.2 or later. Install Groonga first, for example:

    $ brew install groonga                 # macOS
    $ sudo apt-get install libgroonga-dev  # Ubuntu, from ppa:groonga/ppa

Without Groonga, rroonga builds it from the source, which takes a while. See [the install guide of Groonga](https://groonga.org/docs/install.html) for other systems.

Then add this line to the Gemfile of your ROMA server:

```ruby
gem 'roma-storage-groonga'
```

And then run `bundle install`. Or install it yourself:

    $ gem install roma-storage-groonga

## Usage

In the config.rb of ROMA, require the storage and set it to `STORAGE_CLASS`:

```ruby
require 'roma/storage/groonga'

module Roma
  module Config
    # ...
    STORAGE_CLASS = Roma::Storage::GroongaStorage
    # ...
  end
end
```

Each node keeps its data in `STORAGE_PATH/<node-id>/<hash-name>/`, divided into `STORAGE_DIVNUM` Groonga databases named `0.grn`, `1.grn` and so on. Groonga writes some more files next to each of them.

## Development

Run `bundle install`, then `bundle exec rake spec` to run the tests.

## License

GPL-3.0. See LICENSE.txt.
