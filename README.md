# docker-burned-area

Dockerfile for the 

## Using this container

### Getting the help context

```console
docker run --rm -it terradue/nb-burned-delineation:latest burned-area-delineation --help
```

Will return:

```
usage: burned-area-delineation [-h] [--kernel KERNEL] [--output NB_TARGET] [--docker DOCKER] [--cwl] [--params] [--pre_event PRE_EVENT] [--post_event POST_EVENT] [--ndvi_threshold NDVI_THRESHOLD] [--ndwi_threshold NDWI_THRESHOLD]

Burned area delineation Burned area delineation using two techniques

optional arguments:
  -h, --help            show this help message and exit
  --kernel KERNEL       kernel for notebook execution
  --output NB_TARGET    output notebook
  --docker DOCKER       Sets the docker image for the CWL DockerRequirement
  --cwl                 Prints the CWL script and exits
  --params              Prints the default parameters and exits
  --pre_event PRE_EVENT
                        Pre-event product for burned area delineation
  --post_event POST_EVENT
                        Post-event product for burned area delineation
  --ndvi_threshold NDVI_THRESHOLD
                        NDVI difference threshold
  --ndwi_threshold NDWI_THRESHOLD
                        NDWI difference threshold
```
  
### Getting the Common Workflow Language (CWL) script

```console
docker run --rm -it terradue/nb-burned-area-delineation:latest burned-area-delineation --cwl --docker terradue/nb-burned-area-delineation:latest
```
### Getting the Common Workflow Language (CWL) default parameters 

```console
docker run --rm -it terradue/nb-burned-area-delineation:latest burned-area-delineation --params
```

### Executing the CWL script

Get the CWL script:

```console
docker run --rm -it terradue/nb-burned-area-delineation:latest burned-area --cwl --docker terradue/nb-burned-area-delineation:latest > burned-area.cwl
```

Get the parameters:

```console
docker run --rm -it terradue/nb-burned-area-delineation:latest burned-area-delineation --params > burned-area-delineation.yml
```

Execute the CWL script with `cwltool`:

```console
cwltool burned-area-delineation.cwl#burned-area-delineation burned-area-delineation.yml
```
