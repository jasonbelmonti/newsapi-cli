# News API CLI
A [nodejs](https://nodejs.org/)-powered command-line interface for [News API](https://newsapi.org/).

[`sources`](#sources) :arrow_right: [/sources](https://newsapi.org/docs/endpoints/sources)

[`everything`](#everything) :arrow_right: [/everything](https://newsapi.org/docs/endpoints/everything)

[`top-headlines`](#topHeadlines) :arrow_right: [/top-headlines](https://newsapi.org/docs/endpoints/top-headlines)

## Getting Started

### Install dependencies
```
computer-1:repositories user$ cd news-api-cli
computer-1:news-api-cli user$ npm install
```

### Make `news.js` executable
```
computer-1:news-api-cli user$ chmod +x news.js
```

### Add News API Key
Get a key [here](https://newsapi.org/register).

Add a file called `.env` in the project root containing your News API key.

```
// contents of news-api-cli/.env
NEWS_API_KEY=YOUR-KEY-HERE
```

## Commands

### [Sources](https://newsapi.org/docs/endpoints/sources)

#### Usage

`sources [options]`

#### Options
```
-l, --language [language]  Only return articles written in this language
-v, --verbose              If enabled, show description, url, category, language, country
-c, --category [category]  Only return articles relevant to this category
-w, --write [path]         Save the result to [path] (utf-8 encoding)
-h, --help                 output usage information
```
#### Examples

##### Get all english language sources and write them to `sources.json`:
```
./news.js sources -l en -w sources.json
```

##### Get all "business" sources and save to `sources/business.json`:
```
./news.js sources -c business -w sources/business.json
```

##### Get all sources and print all information:
```
./news.js sources -v
```

### [Everything](https://newsapi.org/docs/endpoints/everything)

#### Usage
`everything [options] [query]`

#### Options:
```
-f, --from [from]           Articles published after date This should be in ISO 8601 format (e.g. 2018-07-07 or 2018-07-07T01:07:36)
-t, --to [to]               Articles published before date. This should be in ISO 8601 format (e.g. 2018-07-07 or 2018-07-07T01:07:36)
-s, --sources <sources>     A list of comma-separated news source ids
-p, --pages <pages>         Number of pages to fetch
-z, --page-size <pageSize>  Number of results per page (max 100)
-v, --verbose               If enabled, show url
-l, --language [language]   Only return articles written in this language
-o, --order [order]         order by "relevancy", "popularity", or "publishedAt"
-w, --write [path]          Save the result to [path]
-h, --help                  output usage information
```

#### Examples

##### Get up to 400 articles (4 pages of 100 results each) matching the query "gun control" from [The New York Times](https://www.nytimes.com/) from 05/01/2017 to 06/01/2017 and save to `nyt.json`:
```
./news.js everything gun control -s the-new-york-times -f 2018-05-01 -t 2018-06-01 -p 4 -z 100 -w nyt.json
```

### [Top Headlines](https://newsapi.org/docs/endpoints/top-headlines)

#### Usage
`topHeadlines [options] [query]`

#### Options:
```
-u, --country [country]     Only return articles relevant to this country
-c, --category [category]   Only return articles relevant to this category
-s, --sources <sources>     A list of comma-separated news source ids
-p, --pages <pages>         Number of pages to fetch
-z, --page-size <pageSize>  Number of results per page (max 100)
-v, --verbose               If enabled, show url
-w, --write [path]          Save the result to [path]
-h, --help                  output usage information
```

#### Examples

##### Get top headlines in the United States
```
./news.js topHeadlines -u us
```

##### Get top business headlines in China matching the query "Apple"
```
./news.js topHeadlines Apple -u ch -c business
```
