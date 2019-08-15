FROM rocker/binder:3.6.0
LABEL maintainer='Jeffrey Perkel'
USER root
COPY . ${HOME}
RUN chown -R ${NB_USER} ${HOME}
USER ${NB_USER}
RUN wget https://github.com/jperkel/Mapping_tools_holepunch/raw/master/DESCRIPTION && R -e "options(repos = list(CRAN = 'http://mran.revolutionanalytics.com/snapshot/2019-08-15/')); devtools::install_deps()"
