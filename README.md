# Pensumliste PGR301 

## FLOW 

* Prinsipper for flow. 
* Hva er "Waste" eksempler på dette i systemutvikling? 
* Forstå viktigheten av å bekgrense oppgavestørrelse, og "One piece flow"
* Forstå hvorfor vi forsøker å redusere antall overleveringer i DevOps
* Hvordan kan man gjøre arbeid synlig ? JIRA, Trello osv

### CI

* Bruk gjerne Spring Initializer - https://start.spring.io - lag en Spring Boot app
* Lag et nytt repository på GitHub
* GitHub Branch protection 
* GitHub Status-sjekker.
* GitHub Godkjenning før Merge
* Lage pipeline med GitHub actions som kjører maven, unit tester og bygger jar
* Pipeline skal feile ved kompileringsfeil, enhetstest-feil
* Registrere Repository secrets I et GitHib repository, bruke disse fra en GitHub ACtions workflow/pipeline

### DOCKER 

* Lag Dockerfile som kompilerer applikasjon og lager et Container image
* Grunnleggende docker build, start, run, ps & run
* Docker port mapping
* Docker tag
* Push docker image til Docker Hub 
* Push docker image til Amazon ECR

### DOCKER / CD

* Bruk docker login til å autentisere docker mot AWS ECR 
* Bruk AWS og tjenesten ECR til å lage et repository for ditt container image
* Kjør Docker build, 
* La en GitHub actions Workflow publisere et nytt container image til ECR for hver commit på main branch 
 
### AWS 

* IAM – Finne din egen bruker I IAM
* IAM -Vite hvordan man lager Aceess Keys
* S3 – Vite hvordan du finner State bucket, lage egen bucket
* ECR – Lage/finne repositories for dine bygg
* Ved å bruke AWS UI/Console, Lag en Apprunner Service som kontinuerlig deployer dit container image hver det oppdateres
* Vite hva AWS SAM er og hva det kan brukes til 

### Terraform IAC 

* Forståelse for  Terraform AWS provider
* Terraform resource, variabel og provder
* Terraform variabler, typer og defaultverdier
* Gi terraform variabler fra CLI  forks ```terraform apply --var="student_name=glennbech"```
* Kjør terraform init, fmt, validate, plan, apply, destroy uten backend
* Forstå hva state filen sin hensikt er
* Lag en s3 Backend I provider konfigurasjon for å lagre state i S3 bucket
* Lage pipeline som kjører  Terraform i fra GitHub actions.

### Kontroll på egen PC/mac

* AWS CLI Installasjon
* AWS configure
* Docker
* Maven, Java SDK & Spring Boot, mvn spring-boot:run

## Feedback 

### Prinsipper for feedback

* Se problemer når de oppstår- og løse små problemer før de blir større. 
* Tenk på et samlebånd der deler på en stasjon plutselig har feil. I Toyota production system stopper de hele produksjonen for å finne rot-årsak, hvis feilen ikke en konsekvent og kan løses lokalt på kort tid - Hva betyr dette prinsippet i en Software kontekst? 
* Kvalitet skal oppstå ved kilden. I DevOps fokuserer man på å øke kvaliteten på kode som skrives, ikke på QA og test for å kompansere for dårlig kvalitet. 
* I DevOps automatiserer man så mye som mulig, inkludert prosesser for QA. 

### Spring boot  & Metrisc med Micrometer

* Vite hvordan man bruker Gauge, Counter, og @Timed
* Legge til nødvendige avhengigheter i pom.xml for å legge til Metrics i koden som sendes til AWS CloudWatch 
* Se på CloudWatch metrics i AWS, forstå hvordan man viser grafer og hvilke matematiske funksjoner som passer for de ulike type metrikker
* Lage CloudWatch Dashboard

## Alarmer 

* Lage CloudWatch Alarm basert på en metrikk 
* Forstå prinsippene for en alarm. Metrikk, terskelverdi, antall brudd, tidsperiode
* Sende Alarm til SNS Topic
* Lage en subscription på en SNS topic som sender en alarm til epost, http eller valgfritt endepunkt. 
