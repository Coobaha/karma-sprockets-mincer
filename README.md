# karma-sprockets-mincer

Serve assets developed for Sprockets with Mincer

## Installation

Add `karma-sprockets-mincer` as a devDependency in your `package.json`.
```json
{
  "devDependencies": {
    "karma": "",
    "karma-sprockets-mincer": ""
  }
}
```

or

```bash
npm install karma-sprockets-mincer --save-dev
```

## Configuration

Add the plugin to your config file.

```coffeescript
  plugins: [
    'karma-phantomjs-launcher'
    [...]
    'karma-sprockets-mincer'
  ]
```

Then add `sprockets-mincer` to the top of the frameworks list (order is important).

```coffeescript
frameworks: [
  "sprockets-mincer"
  "jasmine"
]
```

Next, configure the paths that the Sprockets (Mincer) environment should know about.
```coffeescript
sprocketsPaths: [
  'app/assets/javascripts'
  'lib/assets/javascripts'
  'vendor/assets/javascripts'
]
```

Then, configure the js bundle files that Sprockets should generate. These files will be regenerated whenever a sprockets environment file changes.
```coffeescript
sprocketsBundles: [
  'application.coffee'
]
```

You can also add sprockets paths from RubyGems if you are using this in a Ruby/Rails project.

```coffeescript
# "gem-name": ["array of", "sprockets paths"]
rubygems: {
  "rails-widget": ["lib/assets/javascripts", "vendor/assets/javascripts"]
  "jquery-rails": ["vendor/assets/javascripts"]
}
```

This will run grab the path of the bundled gem by running `bundle show` and add them with the specified paths to Sprockets/Mincer.