# Advanced Helm

## 1. Customizing Charts with Helm Templates

__Why we need Helm Templates?__

The change of values such as image version, app version, etc hardcoded is not a good practice. Because of this, is neccesary the use of a templating engine that do this work for us automatically.

Also, if we want to install two version of the same application, we need to use different names for the app artifacts.

![Helm Releases](../images/115.png)

__Helm Template Engine__

![Helm Template Engine](../images/116.png)

![Go Template Engine](../images/117.png)

Helm Template Engine is actually based on Go Template Engine. The values used in Helm Template Engine are coming from different sources.

![Helm Template Engine](../images/118.png)

__Helm Template Execution__

![Helm Template Execution](../images/119.png)

The values used can be get using:

```
$ helm get <<release-name>>
```

Are too in the tiller configmap, bat are shown hardcoded