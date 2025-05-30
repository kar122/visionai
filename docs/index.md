<p align="center">
  <a href="https://docs.visionify.ai"><img src="https://raw.githubusercontent.com/visionify/visionai/main/docs/img/visionai-toolkit-by-visionify.png" alt="VisionAI Toolkit by Visionify"></a>
</p>
<p align="center">
    <em>VisionAI Apps for Workplace Safety. Pretrained & Ready to deploy. </em>
</p>
<p align="center">
<!-- <a href="https://github.com/visionify/visionai/actions/workflows/codeql.yml" target="_blank">
    <img src="https://github.com/visionify/visionai/actions/workflows/codeql.yml/badge.svg" alt="CodeQL">
</a> -->
<a href="https://github.com/visionify/visionai/blob/main/.github/workflows/docs.yaml" target="_blank">
    <img src="https://github.com/visionify/visionai/actions/workflows/docs.yaml/badge.svg" alt="Documentation">
</a>
<a href="https://dev.azure.com/visionify/workplace-safety/_build/latest?definitionId=5&branchName=main" target="_blank">
    <img src="https://dev.azure.com/visionify/workplace-safety/_apis/build/status/visionify.visionai?branchName=main" alt="Test Status">
<a href="https://pypi.org/project/visionai" target="_blank">
    <img src="https://img.shields.io/pypi/v/visionai?color=%2334D058&label=pypi%20package" alt="Package version">
</a>
</p>

---

**Documentation**: <a href="https://docs.visionify.ai" target="_blank">https://docs.visionify.ai</a>

---

## Overview

**VisionAI** offers a collection of pre-trained apps tailored for workplace safety use cases. Developed by **Visionify** as part of the **Workplace Safety** suite, VisionAI is ready for production deployment and accessible through both CLI and web-based GUI.

Key features of **VisionAI** include:

- **No hardware installation**: Works with any IP/security cameras using RTSP streams. No need to install any new cameras, sensors, or other hardware.

- **User-friendly**: Easy-to-use web and CLI interfaces for managing cameras and associated apps, catering to both technical and non-technical users.

- **Production-ready**: Apps are trained on diverse, carefully curated datasets from industrial and academic sources, ensuring out-of-the-box functionality.

- **Azure Marketplace Solution**: Supports Azure VMs, Azure ARC VMs, Azure IoTEdge, and Azure AKS service, enabling scalable enterprise installations for numerous cameras and apps.

- **Customizable**: Allows app customization and model fine-tuning with a flexible architecture based on the NVIDIA Triton server. Refer to customization documentation for more details.

- **Integrations**: Seamlessly integrates with Azure Event Hubs, Redis PubSub, and InfluxDB for reporting, alerts, and notifications, with plans to support additional message brokers.


- **Integrations**: VisionAI currently integrates with Azure Event hubs, Redis PubSub and InfluxDB time-series database for reporting, alerts and notifications. We have roadmap plans to add support for other message brokers as well.


## VisionAI Apps

VisionAI offers a variety of workplace health and safety scenarios, with continuous development of new use cases. View the complete list of over 60 VisionAI Apps [here](scenarios/index.md). If you require a specific scenario not listed here, feel free to [contact us](company/contact.md).

Our primary focus is on workplace health and safety models, but we are expanding our scope to include Quality Inspection, Food Safety/Debris Detection, and more. These additional scenarios are available to customers on a case-by-case basis.


![VisionAI Scenarios](https://raw.githubusercontent.com/visionify/visionai/main/docs/img/VisionAI-Workplace-Safety-Scenarios.png "VisionAI Scenarios for Workplace Safety")


## Quick Start

### Prerequisite

#### Docker

=== "Windows"
    - Install **Docker Desktop** for Windows<br>
    Download the latest version of Docker Desktop from the official website and install it on your Windows machine. This will automatically install Docker Engine and Docker Container for WSL Ubuntu.


=== "Ubuntu"
    - Install Docker Engine and Docker tools<br>
            Open a terminal window and run the following commands to install Docker Engine, Docker CLI, Docker Compose, and Docker Buildx plugin:
        ```console
        sudo chmod a+r /etc/apt/keyrings/docker.gpg
        sudo apt-get update
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
        ```
    - Grant permissions to Docker<br>
        Run the following command to grant permissions to Docker:
        ```console
        sudo chmod 666 /var/run/docker.sock
        ```
        This will avoid the error that may occur during fetching the server API version.
        
=== "MacOS"
    - Get Docker installer for Mac Desktop from [here](https://docs.docker.com/desktop/install/mac-install/)
    - Follow the on-screen instructions to install Docker Desktop for Mac.

#### Disc Space

VisionAI application uses Docker containers to run the apps. The Docker images are large in size and require a minimum of 50GB of free space on the host machine.

#### GPU

VisionAI is a Video-based AI platform that uses GPU for inference. It is recommended to use a GPU with at least 8GB of memory for optimal performance. VisionAI supports NVIDIA GPUs only - Following are a few recommended options:

- NVIDIA GeForce RTX 2060/RTX 2060 Ti
- NVIDIA GeForce RTX 3050/RTX 3050 Ti
- NVIDIA P40
- NVIDIA A100

#### Internet Connectivity

During initial download and setup portion of VisionAI application, we would need good internet connectivity in order to download the required dependencies and Docker containers. Once the setup is complete, VisionAI can be used offline.


---

### Installtion

* Install **VisionAI** through `PyPI`:

<div class="termy">

```console
$ pip install visionai
---> 100%
Successfully installed visionai
```

</div>

* Update to the latest version, if already installed:

``` bash
$ pip install --upgrade --force-reinstall visionai
```

* Initialize VisionAI to download and install dependencies (Docker, Pytorch, NVIDIA Triton, etc.):

``` bash
$ visionai init
```

* Upon successful initialization, you should be able to see the following services running:

---
| Service           | Port                     | Purpose                                         |
| :---------------- | :------------------------| :---------------------------------------------- |
| `Web UI`          | `http://localhost:3001`  | VisionAI Web-app                                |
| `Web API`         | `http://localhost:3002`  | VisionAI API service                            |
| `Triton HTTP`     | `http://localhost:8000`  | Triton Model server (http)                      |
| `Triton GRPC`     | `grpc://localhost:8001`  | Triton Model server (grpc)                      |
| `Triton Metrics`  | `http://localhost:8002`  | Triton Model metrics server (prometheus)        |
| `Redis`           | `redis://localhost:6379` | Redis server, currently supports PUBSUB         |
| `Grafana`         | `http://localhost:3003`  | Grafana server for charting & graphing          |

---


## VisionAI CLI


### Cameras

* List cameras
``` bash
$ visionai camera list
```

* Add/remove cameras through the following commands.

``` bash
$ visionai camera add --name OFFICE-01 --url rtsp://192.168.0.1:554/1
$ visionai camera remove --name OFFICE-01
```


### VisionAI Apps

* List available VisionAI Apps:

``` bash
$ visionai scenario list
```

![VisionAI Scenarios CLI Output](https://raw.githubusercontent.com/visionify/visionai/main/docs/img/visionai-scenarios-list.jpg "VisionAI scenarios CLI output")


* Run a VisionAI App:

``` bash
$ visionai scenario run ppe-detection                          # Web-cam
$                           --camera rtsp://192.168.0.1:554/1   # RTSP camera
$                           --video /path/to/video.mp4          # Video file/youtube link
```


* Get details about an app:

<div class="termy">

``` console
$ visionai scenario details ppe-detection

------------------------------------------------
Category: Fire safety
Scenario: early-smoke-and-fire-detection
This scenario has been trained on open-source datasets consisting of 126,293 images. The datasets images are primarily outdoors (70%), but do contain a good number of indoor images (30%). There is a ~50-50% mix of day vs night images. You can find more details about this scenario at visionify.ai/early-smoke-and-fire-detection.


Model: smoke-and-fire-detection-1.0.1.pt
Model size: 127MB
Model type: Object Detection
Framework: PyTorch

Model performance:
Dataset size: 126,293 images
Accuracy: 94.1%
Recall: 93%
F1-Score: 93.5%

Events:
smoke-detected  | Immediate
fire-detected   | Immediate

Event examples:
{
    "scenario": "smoke-and-fire-detection",
    "event_name": "smoke-detected",
    "event_details": {
        "camera": "camera-01",
        "date": "2023-01-04 11:05:02",
        "confidence": 0.92
    }
}
------------------------------------------------

```
</div>



### VisionAI Models

VisionAI models are automatically started & stopped as needed. You may want to see their status for debug purposes, you can use the following commands.

* List models being served by VisionAI:

``` bash
$ visionai models list
```

![VisionAI Models List CLI Output](https://raw.githubusercontent.com/visionify/visionai/main/docs/img/visionai-models-list.png "VisionAI Models List CLI Output")

* Start or stop serving models.

``` bash
$ visionai models serve
$ visionai models stop
```

### VisionAI Pipelines

Pipelines allow running multiple scenarios on a group of cameras. You can use the following commands to manage pipelines.

* List pipelines:

``` bash
$ visionai pipelines list
```

* Create a pipeline

``` bash
$ visionai pipeline create --name test-pipeline
```

* Add cameras to a pipeline

``` bash
$ visionai pipeline add-camera --name test-pipeline --camera OFFICE-01
$ visionai pipeline add-camera --name test-pipeline --camera OFFICE-02
```

* Add scenarios to a pipeline

``` bash
$ visionai pipeline add-scenario --name test-pipeline --scenario ppe-detection
$ visionai pipeline add-scenario --name test-pipeline --scenario face-blur
$ visionai pipeline add-scenario --name test-pipeline --scenario smoke-and-fire-detection
```

* Start a pipeline

``` bash
$ visionai pipeline start --name test-pipeline
```


### Get help on any command

You can get help on any command by using the `--help` flag.


<div class="termy">

```console

$ visionai pipeline --help

 Usage: visionai pipeline [OPTIONS] COMMAND [ARGS]...

 Manage pipelines
 Pipeline is a sequence of preprocess routines and
 scenarios to be run on a given set of cameras. Each
 pipeline can be configured to run specific scenarios -
 each scenario with their own customizations for event
 notifications. This module provides robust methods for
 managing pipelines, showing their details, adding/remove
 cameras from pipelines and running a pipeline.

╭─ Options ────────────────────────────────────────────────╮
│ --help          Show this message and exit.              │
╰──────────────────────────────────────────────────────────╯
╭─ Commands ───────────────────────────────────────────────╮
│ add-camera      Add a camera to a pipeline               │
│ add-preprocess  Add a preprocess routine to a pipeline   │
│ add-scenario    Add a scenario to a pipeline             │
│ create          Create a named pipeline                  │
│ remove-camera   Remove a camera from a pipeline          │
│ reset           Reset the pipeline to original state.    │
│ run             Run a pipeline of scenarios on given     │
│                 cameras                                  │
│ show            Show details of a pipeline               │
╰──────────────────────────────────────────────────────────╯


```

</div>



## VisionAI Web Application
- VisionAI also supports a web-based option for managing cameras, scenarios and pipeline. You can run the following command to start the web-based GUI. Once the web-based GUI is started, you can access it at http://localhost:3001.

``` bash
$ visionai web start

Web service API available at: http://localhost:3002
Web app available at: http://localhost:3001
```


- This would show an initial screen similar to this:

![VisionAI Web Application](https://raw.githubusercontent.com/visionify/visionai/main/docs/img/visionai-scenarios-web.jpg "VisionAI Web Application").

- You can manage cameras, scenarios, pipelines, see events etc., directly on the web-app. The web-app is running your own local compute instance. All the data is saved in your machine, and it is persistent as long as VisionAI application is not uninstalled.

## Events

VisionAI supports a variety of events that can be used to trigger actions. Our primary mode of events is through PubSub mechanism. VisionAI supports redis pubsub, and Azure Event Hub for posting events. These can be later extended to support emails alerts, SMS alerts, and other mechanisms.

Each event is in the form of a JSON object. The following is an example of an event that is posted when a smoke is detected by the smoke-and-fire-detection scenario.

```json
{
    "camera": "camera-01",
    "scenario": "smoke-and-fire-detection",
    "event_name": "smoke-detected",
    "event_details": {
        "camera": "camera-01",
        "date": "2023-01-04 11:05:02",
        "confidence": 0.92
    }
}
```

To listen to events, you can subscribe to the redis pubsub mechanism as follows:

```python

import redis
r = redis.Redis(host='localhost', port=6379, db=0)
p = r.pubsub()
p.subscribe('visionai')
for message in p.listen():
    print(message)

```

## Redis/Grafana
- VisionAI supports out-of-box integration with Redis, Prometheus, Grafana and Azure Event Hub. Once the web-app is started, you can view the Grafana dashboard at: http://localhost:3003. The default username and password is `admin`/`admin`.

``` bash
Grafana server is at: http://localhost:3003
Redis server is at: redis://localhost:6379
```



## Azure Managed App

Deploy a fully configured and tested solution directly from Azure Marketplace.

**VisionAI** runs computer vision models, most of which run orders of magnitude faster if executed on a GPU machine. Our Azure Marketplace offer **VisionAI Community Edition** is available through Azure Marketplace [here](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/visionifyai1673030402210.visionifyai?tab=Overview). The community edition deploys a fully configured Virtual Machine with the recommended hardware and software options.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/visionifyai1673030402210.visionifyai?tab=Overview)

## Next steps

Congratulations! You have successfully configured and used VisionAI toolkit. Now go through [Tutorials](tutorials/index.md) to learn about how to run multiple scnearios, how to configure each scenario for the events you need, how to set up pipelines with multiple cameras and scenarios.

Or you can also browse through our [scenarios](scenarios/index.md) section to understand different use-cases that are supported currently. If you have a need for a scenario, do not hesitate to submit a [request](https://github.com/visionify/visionai/issues) here.
