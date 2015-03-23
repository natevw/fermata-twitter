# fermata-twitter

**NOTE**: the currently-published fermata@0.10.6 already bundles this plugin, this is split out for an upcoming version!

This is a Twitter API plugin for [Fermata](https://github.com/natevw/fermata). It takes care of just a few boring bits, leaving you with raw unfettered Fermata-style direct usage of the bona fide Twitter API.


## Setup

This is a standard [Fermata plugin](https://github.com/natevw/fermata#plugins), so please see that documentation or take a look at the the [Fermata CouchDB plugin docs](https://github.com/natevw/fermata-couchdb#setup) for example setup.


## Example usage

Here's a summary of the (more complete) "examples/shoutout.js" file you can find in this repo:

    var twapi = fermata.twitter(OAUTH_CREDENTIALS);
    
    twapi.statuses.home_timeline.get(function (e, d) {
      if (e) console.error(e,d);
      else console.log("Timeline:", d);
    });
    
    twapi.statuses.update.post({
      status: "I'm trying out @natevw's Fermata (https://github.com/natevw/fermata) via his Twitter plugin."
    }, function (e,d) {
      if (e) console.error(e,d);
      else console.log("Post result:", d);
    });

    
## Plugin API

The following documentation assumes this plugin has been registered into `'fermata'` with the name `'twitter'`:

- `fermata.twitter(oauth_credentials)` — Returns a "URL proxy" object for Twitters's API (at "https://api.twitter.com"). You must pass an object for `oauth_credentials` including at least your app's `client` and `client_secret` values (for access to their public and OAuth flow APIs) and possibly a `token` and `token_secret` for a user (for APIs requiring access on their behalf).

Behind the scenes, this plugin sets a few necessary headers and **adds the ".json" extension to URLs for you**. But beyond that, it's simply [standard Fermata usage](https://github.com/natevw/fermata#complete-documentation) as you talk to [Twitter's standard API](https://dev.twitter.com/docs/api) — by design!


## License (MIT)

Copyright © 2011–2015 Nathan Vander Wilt.

Released under the terms of the MIT License:

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
