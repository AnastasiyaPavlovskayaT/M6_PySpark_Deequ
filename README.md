# M6_PySpark_Deequ Home Task

## Environment setup:
1. Install Docker on Windows https://docs.docker.com/desktop/windows/install/
2. Clone repository https://github.com/jupyter/docker-stacks
3. Rebuild docker "pyspark-notebook" image to support spark 3.0.0 version for PyDeequ needs according to instructions: https://jupyter-docker-stacks.readthedocs.io/en/latest/using/specifics.html
Please pay attention with java version, should be 8!

```docker build --rm --force-rm -t jupyter/pyspark-notebook:spark-3.0.0 ./pyspark-notebook --build-arg spark_version=3.0.0 --build-arg spark_checksum=bfe45406c67cc4ae00411ad18cc438f51e7d4b6f14eb61e7bf6b5450897c2e8d3ab020152657c0239f253735c263512ffabf538ac5b9fffa38b8295736a9c387 --build-arg openjdk_version=8```

4. Run rebuilt docker image :

```docker run -v $(pwd):/home/jovyan/work -p 8888:8888 -p 4040:4040 --add-host host.docker.internal:host-gateway --user root -e JUPYTER_ENABLE_LAB=yes --name pyspark jupyter/pyspark-notebook ```

5. Copy nessessary JDBC driver to cd running Docker container for the further usage.

```docker cp sqljdbc42.jar 923d5ce18ac1:/home/jovyan/work```

## JupiterLab run

1. Run pyspark-notebook docker container.
2. Open url to JupiterLab run. Url can be found in the docker run log.
3. Change connection string variables for correct to machine.
4. Open ```Deequ_pySpark_ HomeTask.ipynb``` and run all cells.

## Test result

Open ```verification_report.html``` in tha any webbrowser.
