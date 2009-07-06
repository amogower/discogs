Discogs::Wrapper
================

ABOUT
-----
  A 100% Ruby wrapper of the Discogs.com API. No dependencies, no extra gems. :)

  Discogs::Wrapper abstracts all the nasty boilerplate code needed to interact with the Discogs API. It gives you direct access to the information you need.

  Full support for everything in version 1.0 of the API:

  * Artists
  * Releases
  * Labels
  * Searching

  The API is [documented here](http://www.discogs.com/help/api).

INSTALLATION
------------
  You can install the library via Rubygems:
    $ gem sources -a http://gems.github.com
    $ sudo gem install buntine-discogs

USAGE
-----
  To use this library, you must supply a valid Discogs API key.
    require 'discogs'

    wrapper = Discogs::Wrapper.new("my_api_key")

  Accessing information is easy:
    artist = wrapper.get_artist("Master's Hammer")
    release = wrapper.get_release("611973") # Supply an ID.
    label = wrapper.get_label("Monitor Records")
    search_results = wrapper.search("Necrovore")

    artist.name                         # => "Master's Hammer"
    artist.releases[0].title            # => "Finished"
    artist.releases[1].year             # => "1989"
    artist.releases[4].extraartists     # => [ "Arakain", "Debustrol" ]

    release.title                       # => "Ritual"
    release.labels[0].name              # => "Osmose Productions"
    release.formats[0].descriptions[0]  # => "LP"
    release.styles                      # => [ "Black Metal", "Death Metal" ]
    release.tracklist[1].title          # => "Pad modly"

    label.images[0].width               # => "220"
    label.releases.length               # => 22
    label.releases[3].artist            # => "Root"
    label.releases[7].catno             # => "MON007"

    search.total_results                # => 124
    search.exactresults[0].type         # => "artist"
    search.exactresults[0].title        # => "Necrovore"
    search.searchresults[3].title       # => "Necrovore - Demo '87"
    search.searchresults[3].summary     # => "First and only demo tape"