# Quick Start

## **Installing earthaccess**

The latest release of `earthaccess` can be installed with `mamba`, `conda` or `pip`.  We recommend using `mamba` because it is faster.

You will need Python 3.8 or higher installed.

#### Using `mamba`

```bash
mamba install -c conda-forge earthaccess
```

#### Using `conda`

```bash
conda install -c conda-forge earthaccess
```

#### Using `pip`

```bash
pip install earthaccess
```


### Check `earthaccess` is installed

This should run seamlessly (fingers-crossed).  To check `earthaccess` is correctly installed you can start a python interpreter (either python or ipython) and run the following code.

```
$ python
Python 3.12.1 | packaged by conda-forge | (main, Dec 23 2023, 08:03:24) [GCC 12.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import earthaccess
>>> earthaccess.__version__
'0.8.2'
```

> Note:
> Your `python` and `earthaccess` versions may be different.


## **Get Data in 3 Steps**

`earthaccess` allows you to search for and access data in as little as three steps.  We give a very quick example below.  These three steps allow you to get data whether you are working in the cloud or on your local laptop or workstation.  Read the [User Guide](user_guide.qmd) for more information.  If you want to quickly find how to perform some common searches and data access,
take a look at our [How-to](how_to.qmd) guide.

The only requirement to use this library is to open a free account with NASA [EDL](https://urs.earthdata.nasa.gov).

### Step 1: Login

To access NASA data, you have to login using your Earth Data Login credentials.  You can register for a free Earth Data Login account [here](https://urs.earthdata.nasa.gov/).

By default, `earthaccess` will look for your Earth Data Login credentials in a `.netrc` file, or in environment variables `EARTHDATA_USERNAME` and `EARTHDATA_PASSWORD`.  If you don't
have either of these set up, you can login manually.  See [Authenticating](authenticate.qmd) to learn how to create a `.netrc` file or environment variables.

```
import earthaccess

earthaccess.login()
```


### Step 2: Search for data

As an example, we'll search for data from the NASA ICESat-2 mission.  ATL06


```
results = earthaccess.search_data(
    short_name='ATL06'
    bounding_box=(-10, 20, 10, 50),
    temporal=("1999-02", "2019-03"),
    count=10
)
```

### Step 3. Download the files

Once you have found the files you want, you can download them to your local machine.

```
files = earthaccess.download(results, "./local_folder")
```

If you are working in the cloud and the data files are hosted in the cloud, you can stream the data directly, without having to download data.  See [Direct S3 Access]()
