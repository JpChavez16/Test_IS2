# Snap Shot [![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?text=See%20this%20react%20example&url=https://yog9.github.io/SnapShot/&hashtags=react,context-api,freecodecamp,developers)

[![Build Status](https://travis-ci.org/Yog9/SnapShot.svg?branch=master)](https://travis-ci.org/Yog9/SnapShot)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![HitCount](http://hits.dwyl.com/Yog9/SnapShot.svg)](http://hits.dwyl.com/Yog9/SnapShot)

[Demo of Snap Shot](https://yog9.github.io/SnapShot/)

![](/snapscout.png)

### Summary

Snap Shot is a gallery created using React,React Hooks, React Router and Context API. The Routes were setup for four default pages and a search page. Also the images were displayed using the Flickr API and axios to fetch data.

### Motivation

The purpose of this project was to get familiar with React Hooks and Context API.

### Getting Started

Click the demo link or clone/download the repository on your local machine.
Create a config.js file in api folder inside src folders. In config.js file write
`export const apiKey = "YOUR_FLIKR_API_KEY";`

##### Install dependencies

`yarn install`

##### Run Snap Shot from the root directory.

`yarn start`

### Built With

- React js
- React Router
- React Hooks
- Context API
- Flickr API

### Features

**1. Responsive Design.**

**2. Search functionality added to search photos from API.**

### Coming Soon

- [ ] Cypress E2E Tests

### Contributing

Everyone is welcomed to contribute to this project. You can contribute either by submitting bugs or suggesting improvements by opening an issue on GitHub. Please see the [CONTRIBUTING](CONTRIBUTING.md) guidelines for more information.

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).


## Pipeline de CI/CD: Para el Proyecto, implementar un pipeline de CI/CD en Jenkins:

Para el Proyecto, implementar um pipeline de CI/CD en Jenkins: 
<br/>
El codigo se puede ver en el archivo [Jenkins](https://github.com/evargashe/ProyectoIs2/blob/branch-edwar/jenkins/Jenkins)
```
pipeline{
    agent any
    stages{

        stage(" Dependencias y Sonar-Scanner")
        {
            steps{
                nodejs(nodeJSInstallationName: 'nodejs'){
                    bat "npm i && npm ci"
                    withSonarQubeEnv('sonar')
                    {
                        bat "npm install sonar-scanner"
                        bat "sonar-scanner"
                    }
                }
            }
        }
```
El pipeline contiene las siguientes tareas:
<br/>
### Construcción Automática:
Este proyecto ya contaba con una contruccion automatica en [JSON](https://github.com/evargashe/ProyectoIs2/blob/branch-edwar/package.json) para JavaScript.
```
{
  "name": "snapshot",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^4.2.4",
    "@testing-library/react": "^9.3.2",
    "@testing-library/user-event": "^7.1.2",
    "axios": "^0.19.2",
    "react": "^16.13.1",
    "react-dom": "^16.13.1",
    "react-router-dom": "^5.1.2",
    "react-scripts": "3.4.1",
    "sonar-scanner": "^3.1.0"
  },
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "sonar-scanner": "node_modules/sonar-scanner/bin/sonar-scanner.bat"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  }
}
```
<br/>

### Análisis Estático:
Ejecutamos sonarqube desde el pipeline de Jenkins.
- Ejecutar SonarQube localmente
![EjecutarSonar](https://github.com/evargashe/ProyectoIs2/blob/branch-edwar/imgs/SonarUp.JPG)

- Creamos un archivode configuracion en el directorio del proyecto: [sonar-project.properties](https://github.com/evargashe/ProyectoIs2/blob/branch-edwar/sonar-project.properties)
```
sonar.projectKey=proyectoFinalIs2
sonar.projectName=proyectoFinalIs2
sonar.projectVersion=1.0-SNAPSHOT
sonar.source=src/
sonar.sourceEncoding=UTF-8
sonar.host.url=http://localhost:9000
sonar.login=060e5cda987542c8595d5e2f7f8778d818c0b35b
sonar.exclusions=src/*.cssgit 
sonar.javascript.lcov.reportPath=reports/js/cov.dat
```
<br/>
- Instalamos sonar-scanner con el comando.

```
npm install sonar-scanner
```

![Sonar](https://github.com/evargashe/ProyectoIs2/blob/branch-edwar/imgs/scriptjenkinssonar.JPG)
<br/>

- Ejecutamos sonar-scanner con el comando.

```
sonar-scanner
```
![ConsolaSonar](https://github.com/evargashe/ProyectoIs2/blob/branch-edwar/imgs/consolasonarjenkins1.JPG)
<br/>
![ConsolaSonar](https://github.com/evargashe/ProyectoIs2/blob/branch-edwar/imgs/consolasonarjenkins2.JPG)
<br/>

- Visualizar resultados de SonarScanner en SonarQube: en este [PDF](https://drive.google.com/file/d/1VEhhykfUfs77WOSKnlOkXqGUF2TgS_vU/view?usp=sharing)
[http://localhost:9000](http://localhost:9000)

![Sonar](https://github.com/evargashe/ProyectoIs2/blob/branch-edwar/imgs/visualizacionsonarhost.JPG)






