FROM jupyter/datascience-notebook

RUN python --version

USER root

ARG DEBIAN_FRONTEND=noninteractive

# LIBPOSTAL
# Install Libpostal dependencies
RUN apt-get update && \
        apt-get install -y \
                make \
                curl \
                autoconf \
                automake \
                libtool \
                pkg-config \
                python3-pip

# Download libpostal source to /usr/local/libpostal-1.1-alpha
RUN cd /usr/local && curl -sL https://github.com/openvenues/libpostal/archive/v1.1-alpha.tar.gz | tar -xz


# Create Libpostal data directory at /var/libpostal/data
RUN cd /var && \
        mkdir libpostal && \
        cd libpostal && \
        mkdir data

# Install Libpostal from source
RUN cd /usr/local/libpostal-1.1-alpha && \
        ./bootstrap.sh && \
        ./configure --datadir=/var/libpostal/data && \
        make -j4 && \
        make install && \
        ldconfig

RUN conda install --quiet --yes -c \
    conda-forge osmnx dask

RUN pip install -U geopandas \
                   geopy \
                   rtree \
                   folium \
                   numpy \
                   shapely \
                   fiona \
                   six \
                   pyproj \
                   numexpr==2.6.4 \
                   git+https://github.com/CartoDB/cartoframes.git@develop \
                   geojson \
                   plotly \
                   psycopg2 \
                   tqdm \
		       seaborn \
                   geohash2 \
                   tables \
                   mixpanel \
                   SQLAlchemy \
                   gdown \
                   gsutil \
                   pandas-profiling \
                   google==2.0.3 \
                   google-api-core==1.14.3 \
                   google-auth==1.6.3 \
                   google-cloud-bigquery==1.22.0 \
                   google-cloud-bigquery-storage==0.7.0 \
                   google-cloud-core==1.0.3 \
                   google-cloud-storage==1.23.0 \
                   google-resumable-media==0.5.0 \
                   googleapis-common-protos==1.6.0 \
                   GeoAlchemy2 \
		   postal

ADD fonts /usr/share/fonts/truetype/

RUN fc-cache
RUN fc-list

USER root

RUN sudo apt-get update -y && \
    sudo apt-get install -y miller

VOLUME /notebooks
WORKDIR /notebooks
