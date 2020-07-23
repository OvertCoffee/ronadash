# RonaDash

*A system for visualizing the spread and effects of the 2019 novel coronavirus*

## About

The goal of this project is to make information regarding the spread of the 2019 novel coronavirus (aka covid-19, NCoV) more readily accessible to the public and in a more granular context. To better inform day-to-day decisions I'm more interested in what the case rates look like in my region, more than the country as a whole.

## Install

* [Install Docker](https://docs.docker.com/get-docker).

* Clone the [CSSE's data repo](https://github.com/CSSEGISandData/COVID-19), this is used for historic data. Data repo should be adjacent to this repo on the local system (see the volumes specification for data service in docker-compose.yml to adjust)
    * ```git clone https://github.com/CSSEGISandData/COVID-19.git ../COVID-19```

* Rename example.env to .env and fill in values as appropriate for endpoint, email, database credentials, etc.
    * ```ENDPOINT``` - Your domain name. Should work with local DNS resolution / hosts files if hosting on LAN.
    * ```DEVEMAIL``` - Used for tls certificate challenges.
    * ```POSTGRES_*``` - Used for securing the database.

* Start the containers
    * ```docker-compose up -d```

* Navigate to ```ronadash.<endpoint defined in .env>```, change Grafana admin password (admin/admin), and enjoy. 
    * The initial database load usually takes a few minutes, and may vary. Progress can be inspected with e.g. ```docker logs -f ronadash_data_1```

## Credits

* [JHU/CSSE](https://systems.jhu.edu/)
    
    Johns Hopkins University's Center for Systems Science and Engineering (CSSE) provides [publicly-available ncov data](https://github.com/CSSEGISandData/COVID-19) used to load the database on creation.

* [David (aka eusoumaxi)](https://github.com/eusoumaxi)
    
    [This](https://github.com/eusoumaxi/apiCovidData) is the code for the API used to update the database after the initial load.

* [Jeff Kehres](https://github.com/jkehres) 
    
    [This repo](https://github.com/jkehres/docker-compose-influxdb-grafana) was a big help with examples of using grafana with docker compose

* [Christian Martins](https://github.com/Mau5Machine)

    [This gist](https://gist.github.com/Mau5Machine/00401feb19433cf0387cc66c8e90c26c) helped with the traefik config in docker-compose.yml

## Contributing

Pull requests and issues are welcome. Please discuss the changes via issue or email before creating a pull request.

## Data Sources

[Daily Updates](https://corona.azure-api.net/) ([Docs](https://documenter.getpostman.com/view/11787033/SzzoYuSa?version=latest#intro))

[Historical](https://github.com/CSSEGISandData/COVID-19) (initial database load)


## Disclaimer

This project was developed without the assistance of any doctor, epidemiologist, statistician, or government entity. Any insights provided should not be construed as medical or legal advice.
