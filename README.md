# Solr typeahead

![](files/typeahead.gif?raw=true)

* play with solr schema and queries for typeahead
* use NGramTokenizerFactory and EdgeNGramTokenizerFactory to get efficient prefix and case-insensitive query
* refer to https://examples.javacodegeeks.com/enterprise-java/apache-solr/solr-autocomplete-example/

## Setup

most important config file is [schema.xml](files/schema.xml)
`solr-5.0.0/server/solr/arm/conf/schema.xml` and `solrconfig.xml`

Added the following relevant lines (id as primary key must be different) to [books.csv](files/books.csv)
```
0551888303,book,ACCOUNT-112,7.99,true,George R.R. Martin,"A Song of Ice and Fire",1,fantasy
0558888303,book,ACCOUNT-212,7.99,true,George R.R. Martin,"A Song of Ice and Fire",1,fantasy
0552573303,book,ACCOUNT-12,7.99,true,George R.R. Martin,"A Song of Ice and Fire",1,fantasy
0553573303,book,ACCOUNT-11,7.99,true,George R.R. Martin,"A Song of Ice and Fire",1,fantasy
```

## Commands

create index
```shell
solr-5.0.0/bin$ solr create -c arm -d basic_configs
```

update index
```shell
solr-5.0.0/example/exampledocs$ java -Dtype=text/csv -Durl=http://localhost:8983/solr/arm/update -jar post.jar  books.csv
```