# elastic.js

A JavaScript implementation of the [ElasticSearch](http://www.elasticsearch.org/) DSL for use with the [official elasticsearch javascript client](http://elasticsearch.github.io/elasticsearch-js/index.html).  

## Documentation
You can find the official documentation at the following locations:

- [User Guide](http://www.fullscale.co/elasticjs)
- [API Documentation](http://docs.fullscale.co/elasticjs/)

You will also be able to find unofficial documentation and examples on on our
[blog](http://www.fullscale.co/blog/) and GitHub Gist pages [here](https://gist.github.com/mattweber)
and [here](https://gist.github.com/egaumer).

## Examples

### Search

See http://elasticsearch.github.io/elasticsearch-js/api.html#search.

```
client.search({
  index: 'myindex',
  body: ejs.Request()
          .query(ejs.MatchQuery('title', 'test'))
          .facet(ejs.TermsFacet('tags').field('tags'))
}, function (error, response) {
  // handle response
});
```

### Suggest

See http://elasticsearch.github.io/elasticsearch-js/api.html#suggest

```
client.suggest({
  index: 'myindex',
  body: ejs.TermSuggester('mysuggester')
          .text('tset')
          .field('title')
}, function (error, response) {
  // handle suggestion response
});
```

### Multi-Search

See http://elasticsearch.github.io/elasticsearch-js/api.html#msearch

```
client.msearch({
  body: [
    {}
    ejs.Request().query(ejs.MatchAllQuery()),
    { index: 'myindex', type: 'mytype' },
    ejs.Request().query(ejs.QueryStringQuery('"Test 1"'))
  ]
});
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [grunt](http://gruntjs.com/).

_Also, please don't edit elastic.js and elastic.min.js files as they are generated via grunt. You'll find source code in the "src" subdirectory!_

## License
Copyright (c) 2012-2014 FullScale Labs, LLC
Licensed under the MIT license.
