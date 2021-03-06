# discogs-marketplace-js

⚠️ I no longer maintain this forked library. If you are looking for a good library to retrieve data from the Discogs marketplace, check it out here: [Discogs-Marketplace-API-NodeJS](https://github.com/KirianCaumes/Discogs-Marketplace-API-NodeJS) ⚠️

---

JavaScript library to pull information from the Discogs marketplace.  Returns an object.

MY FORK provide more data to the objects returns, and implements a promise as the return the search instead of a callback.

## Usage

### Init

````javascript
var discogsApi = require('discogs-marketplace-js');
````

### Search

````javascript
var params = {
    id: "244819",
    type: "artist",
    country: 'fr', //'en', etc
    pagination : {
        page: 1,
        per_page: 100,
        sort: "Listed Newest"
    }
}
discogsApi.search(params, (res) => {
    console.log(res)
})
//OR
discogsApi.search(params)
    .then(data => console.log(data))
    .catch(err => console.log(err))
````

### Filters/Pagination

To specify search filters and pagination options, discogs-marketplace-js will accept an object as an input.

````javascript
var params = {
    id: "1067610", //id can also be a string, if used with type 'string'
    type: "release", //one of: 'release', 'master', 'label', 'string', OR 'artist' (with artist ID)
    country: 'fr', //'en', etc
    filters: {
        genre: "Rock",
        style: null,
        format: "Vinyl",
        country: "US",
        decade: null,
        condition: ["Very Good Plus", "Mint"],
        year: 2015,
        currency: "USD",
    },
    pagination: {
        page: 1,
        per_page: 25,
        sort: "Price Lowest Highest"
    }
};
````

### Result

````
{
	id: '1067610',
	type: 'master',
	pagination: 
	{ 
		items: 1112, 
		hasNext: true
		totalPages : 0 
	},
  	listing: 
   	[ 
   		{	
   			title: 'Black Sabbath - Black Sabbath (8-Trk, Album)',
			condition_sleeve: 'Very Good (VG)',
			condition_media: 'Very Good (VG)',
			seller: 'easeup',
			ships_from: 'United States',
			price: '$45.00' 
	   },
	   { 
	   		title: 'Black Sabbath - Black Sabbath (2xLP, Album, Dlx, RE, RM, 180)',
			condition_sleeve: 'Near Mint (NM or M-)',
			condition_media: 'Near Mint (NM or M-)',
			seller: 'fishtown19125',
			ships_from: 'United States',
			price: '$35.00' 
		}
	]
}
````

## Installation

```sh
npm install KirianCaumes/discogs-marketplace-js
```
