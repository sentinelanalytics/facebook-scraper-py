# facebook-scraper-py
Facebook scraper made in Python 3 that stores posts, reactions and comments of a page in a Mongo database.

## Dependencies
* Python 3.5.2
* pip: `$ sudo apt-get install python3-pip`
* PyMongo: `$ pip3 install pymongo`
* python-dateutil: `pip3 install python-dateutil`
* urllib3: `pip3 install urllib3`

## Usage
* Create a Facebook app in the [Developer Portal](https://developers.facebook.com/)
* Spin up a MongoDB service in your machine (must be localhost).
* Specify the pages that you want to scrape in a file called `config.json` (not `config.all.json`) at the root of the folder

Your `config.json` must look something like this:
```
{
    "credentials": {
        "appId": "<your-app-id>",
        "appSecret": "<your-app-secret>"
    },
    "pages": [
        {"name": "Noticias Caracol", "id": 216740968376511},
        {"name": "El Tiempo", "id": 148349507804},
        {"name": "El Espectador", "id": 14302129065},
        {"name": "Noticias RCN", "id": 154413711236788},
        {"name": "Revista Semana", "id": 97041406678},
        {"name": "El Heraldo", "id": 21935701184},
        {"name": "Álvaro Uribe Vélez", "id": 45242794557},
        {"name": "Juan Manuel Santos", "id": 330825443903}
    ]
}
```
* The `credentials` object will store the credentials of your app in Facebook.
* The `pages` array requires only the `id` property, which is the ID of the page you want to scrape.
* You can find the page ID by going to [Find my Facebook ID](https://findmyfbid.com/) and entering the link of the page.

The script will create a new Mongo database with the name `facebook` and the following collections:
* `posts`
* `comments`
* `reactions`

Finally, execute `main.py`: `$ ./main.py`
