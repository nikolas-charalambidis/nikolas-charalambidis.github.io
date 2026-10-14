# [nikolas-charalambidis.com](https://nikolas-charalambidis.com/)

## Localhost development

### Prerequisites

- Ruby 3.x (the macOS system Ruby 2.6 does not work), e.g. via Homebrew:
  ```shell
  brew install ruby
  export PATH="/opt/homebrew/opt/ruby/bin:$PATH"   # add to ~/.zshrc to make it permanent
  ```

### Setup

- Install Bundle packages into `vendor/bundle` (git-ignored)
  ```shell
  bundle config set --local path vendor/bundle
  bundle install
  ```
- If native extensions fail to compile (e.g. `ffi`) or Jekyll crashes on Ruby 3.3 (`undefined method '[]' for nil` in `logger.rb`), update the outdated gems
  ```shell
  bundle update ffi jekyll --conservative
  ```

### Build

- Build the site into `_site/`
  ```shell
  bundle exec jekyll build --config _config.yml,_config_development.yml
  ```

### Run

- Deploy on localhost (rebuilds on file changes)
  ```shell
  bundle exec jekyll serve --config _config.yml,_config_development.yml --livereload
  ```
  Served on http://127.0.0.1:4000/gradfolio/ or http://localhost:4000/gradfolio/

## Navigation

- Pages in this repository appear in the navigation when they declare `nav_title` and `nav_order` in their front matter.
- Links to pages hosted in other repositories (CV, Wiki) are defined in `_data/navigation.yml`.
- Set `published: false` to hide a link and stop the page from being built.
- Blog posts and the `projects` collection have separate switches in `_config.yml` (`defaults` for posts, `collections.projects.output`).
