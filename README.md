# Pensumliste PGR301 

## INTRO TIL DEVOPS 

* Hva er DevOps, Hvorfor DevOps funker ; https://kristiania.instructure.com/courses/8662/files/folder/01-intro
* De tre DevOps prinsippene; Flow, Feedback og kontinerlig forbedring 
* DevOps satt i sammenheng med andre metoder som for eksempel smidig og vannfall 

Lab

* Bli kjent med Cloud 9 https://github.com/glennbechdevops/00-welcome-to-cloud9

## FLOW 

Presentasjon

* Prinsipper for flow. https://kristiania.instructure.com/files/931596/download?download_frd=1

Relevante temaer 

* Hva er "Waste" eksempler på dette i systemutvikling? 
* Forstå viktigheten av å bekgrense oppgavestørrelse, og "One piece flow"
* Forstå hvorfor vi forsøker å redusere antall overleveringer i DevOps
* Hvordan kan man gjøre arbeid synlig ? JIRA, Trello osv

### CI

Presentasjon

* Continous integration: https://kristiania.instructure.com/files/931597/download?download_frd=1

Lab 

* https://github.com/glennbechdevops/01-CI-Github-actions

Relevante temaer

* Bruk gjerne Spring Initializer - https://start.spring.io - lag en Spring Boot app
* Lag et nytt repository på GitHub, og sjekk inn koden
* Konfigurer GitHub Branch protection - slik at man må lage en Pull request før merge til main branch
* Slå på GitHub Status-sjekker, slik at maven må bygge, tester kjøre osv før Pull request kan merges til main
* GitHub Pull requrst med godkjenning av andre før Merge til main 
* Pipeline skal feile ved kompileringsfeil, enhetstest-feil
* Clean commits; hvordan bruke git rebase for å ikke få hver eneste commit fra en feature branch inn i main.

GitHub Actions

* Registrere Repository secrets I et GitHib repository, bruke disse fra en GitHub ACtions workflow/pipeline
* Hvordan bruke "on" for å bestemme hva som er trigger for workflow 
* Lage pipeline som kjører maven, unit tester og bygger jar

### Continous Delivery / CD

Presentasjon

* Continous Delivery https://kristiania.instructure.com/files/938002/download?download_frd=1
* AWS Lamda og SLS https://kristiania.instructure.com/files/947525/download?download_frd=1

Lab

* Deployment av AWS Lambda med SAM og Github acitons https://github.com/glennbechdevops/02-CD-AWS-lamda-sls

Relevante temaer

* Hva er AWS Lambda
* Hva er Serverless Framework

### Docker

Presentasjon 

https://kristiania.instructure.com/files/949330/download?download_frd=1

Lab

https://github.com/glennbechdevops/spring-docker-dockerhub

Relevante temaer

* Lag Dockerfile som kompilerer applikasjon og lager et Container image
* Grunnleggende docker build, start, run, ps & run
* Docker port mapping
* Docker tag
* Push docker image til Docker Hub
* Push docker image til Amazon ECR
* Bruk docker login til å autentisere docker mot AWS ECR 
* Bruk AWS og tjenesten ECR til å lage repository for et container image
* La en GitHub actions Workflow publisere et nytt container image til ECR for hver commit på main branch 


### AWS 

* IAM – Finne din egen bruker I IAM
* IAM -Vite hvordan man lager Aceess Keys
* S3 – Vite hvordan du finner State bucket, lage egen bucket
* ECR – Lage/finne repositories for dine bygg
* Vite hva AWS SAM er og hva det kan brukes til 

### Terraform IAC 

Presentasjon

https://kristiania.instructure.com/files/960179/download?download_frd=1

Lab 

https://github.com/glennbechdevops/terraform-app-runner

Relevante temaer 

* Forståelse for Terraform AWS provider
* Terraform resource, variabel og provider
* Terraform variabler, typer og defaultverdier
* Gi terraform variabler fra CLI  forks ```terraform apply --var="student_name=glennbech"```
* Kjør terraform init, fmt, validate, plan, apply, destroy uten backend
* Forstå hva state filen sin hensikt er
* Lag en S3 Backend I provider-konfigurasjon for å lagre state i S3 bucket
* Lage pipeline som kjører Terraform i fra GitHub actions.

AWS App runner

* Ved å bruke AWS UI/Console, Lag en Apprunner Service som kontinuerlig deployer dit container image hver det oppdateres
* Vite hva tjenesten Apprunner gjør 
* Kune lage Terraform-kode for en AWS Apprunner tjeneste 

## Feedback 

### Prinsipper for feedback

Presentasjon 

https://kristiania.instructure.com/files/990060/download?download_frd=1

* Se problemer når de oppstår- og løse små problemer før de blir større. 
* Tenk på et samlebånd der deler på en stasjon plutselig har feil. I Toyota production system stopper de hele produksjonen for å finne rot-årsak, hvis feilen ikke en konsekvent og kan løses lokalt på kort tid - Hva betyr dette prinsippet i en Software kontekst? 
* Kvalitet skal oppstå ved kilden. I DevOps fokuserer man på å øke kvaliteten på kode som skrives, ikke på QA og test for å kompansere for dårlig kvalitet. 
* I DevOps automatiserer man så mye som mulig, inkludert prosesser for QA. 

### Spring boot & Metrics med Micrometer

Presentasjon 

https://kristiania.instructure.com/files/990059/download?download_frd=1

Lab 

https://github.com/glennbechdevops/terraform-cloudwatch-dashboard

* Spring Boot micrometer: Vite hvordan man bruker Gauge, Counter, og @Timed
* Legge til nødvendige avhengigheter i pom.xml for å legge til Metrics i koden som sendes til AWS CloudWatch 
* Se på CloudWatch metrics i AWS, forstå hvordan man viser grafer og hvilke matematiske funksjoner som passer for de ulike type metrikker
* Lage CloudWatch Dashboard
* Lage Terraform-kode som lager Cloudwatch dashboard 
* Lage en GitHub actions pipeline som lager kjører Terraform  

## Alarmer 

Presentasjon

https://kristiania.instructure.com/files/1002528/download?download_frd=1

Lab 

https://github.com/glennbechdevops/cloudwatch_alarms_terraform

* Lage CloudWatch Alarm basert på en metrikk 
* Forstå prinsippene for en alarm. Metrikk, terskelverdi, antall brudd, tidsperiode
* Sende Alarm til SNS Topic
* Lage en subscription på en SNS topic som sender en alarm til epost, http eller valgfritt endepunkt. 
* Lage Terraform-kode som lager Cloudwatch alarm 
