## Personal Website
Personal website make it with Jekyll and hosting on Github Pages.

## Dependencies
- Ruby 2.1.6.
- Jekyll.

## Get started
1. Install the latest version of `ruby` using homebrew, if you hasn't installed homebrew follow the next step first.
```sh
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
2. If you have `homebrew` installed, run the next commands for install `ruby` and verify the `ruby` version.
```sh
$ brew install ruby
$ ruby -v
```
3. Install the project dependencies using bundler.
```sh
$ bundler install
```
4. Serve the project.
```sh
$ bundle exec jekyll serve
```
5. Go to http://localhost:4000.

## Scripts
### Compile Web Components using the Vue CLI service
```sh
$ ./node_modules/.bin/vue-cli-service build --target wc-async --name portfolio 'src/*.vue' --dest assets/js
```

Crafted by Javier Diaz