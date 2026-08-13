source "https://rubygems.org"

# GitHub Pages pins Jekyll and the supported plugin set, so matching it
# locally is what keeps `jekyll serve` honest about what will deploy.
#
#   bundle install
#   bundle exec jekyll serve --config _config.yml,_config.dev.yml
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-sitemap"
  gem "jekyll-redirect-from"
end

# Not bundled with Ruby 3.x, but required by Jekyll.
gem "webrick", "~> 1.8"

gem "wdm", "~> 0.1.1", platforms: [:mingw, :x64_mingw, :mswin]
