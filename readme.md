# Multi-Page Application Archive

Crawls a Multi-Page Application into a zip file. Serve the Multi-Page
Application from the zip file. A MPA archiver. Could be used as a Site
Generator.

## Installation

`npm install -g mpa-archive`

## Usage

### Crawling

`mpa http://example.net`

Will crawl the url recursively and save it in `example.net.zip`. Once
done, it will display a report and can serve the files from the zip.

### Serving

`mpa`

Will create a server for each zip file on the current directory. Host
is `localhost` with a `port` seeded to the zip file path.

## Features

- It uses headless puppeteer
- Crawls `http://example.net` with `cpu count / 2` threads
- Progress is displayed in the console
- Fetches `sitemap.txt` and `sitemap.xml` as a seed point
- Reports HTTP status codes different than 200, 304, 204, 206
- Crawls on site urls only but will `fetch` external resources
- Intercepts site resources and saves that too
- Generates `mpa/sitemap.txt` and `mpa/sitemap.xml`
- Saves site sourcemaps
- Can resume if process exit, save checkpoint every 250 urls

### to consider

- save it in an incremental compression format, that doesnt require
  re-compressing the whole file when it changes, maybe already does
  that?
- urls to externals resources are not re-written to be local
  resources, if this is done then stuff loaded from the root will
  break
- it should crawl the site by clicking the links instead of opening a
  full tab
