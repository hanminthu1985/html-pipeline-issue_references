# HTML::Pipeline::IssueReferences

An HTML::Pipeline filter for auto-linking GitHub issue references.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'html-pipeline-issue_references'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install html-pipeline-issue_references

## Usage

Suppose you have some text that contains references to GitHub issues, like this:

```
Fixes rails/rails#123
```

This filter will automatically transform the GitHub-style issue references into
a bonafide hyperlink to the actual issue. For example, this code:

```ruby
require "html/pipeline"
require "html/pipeline/issue_references"

pipeline = HTML::Pipeline.new [
  HTML::Pipeline::IssueReferenceFilter
]

result = pipeline.call("Fixes rails/rails#123", {
  base_url: "https://github.com",
  repository: "foo/bar"
})

puts result[:output].to_html
```

will output this:

```
Fixes <a href='https://github.com/rails/rails/issues/123' class='issue-reference'>rails/rails#123</a>
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release` to create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

1. Fork it ( https://github.com/codetree/html-pipeline-issue_references/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

## Updating RubyGems
1. Ensure you have the desired branch `git checkout master && git fetch origin && git pull`
2. Create an annotated tag `git tag -a v1.0.1 -m "msg with the tag"`
3. Push tag to Github `github push --tags`
