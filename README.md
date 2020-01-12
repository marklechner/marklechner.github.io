# Workarounds
* Had to manually lock this gem so version 1.0.0 doesn't break the bundleÉ
    - `gem 'faraday', '~> 0'`
* In order to make both local and github pages build/serve function had to define/lock:
    - `gem "jekyll", "~> 3.8.5"`
    - `gem "github-pages","~> 202" , group: :jekyll_plugins`
* Also locked in this plugin:
    - `gem "jekyll-feed", "~> 0.11.0"`

# Build and test locally
* `bundle exec jekyll build`
* `bundle exec jekyll serve`
