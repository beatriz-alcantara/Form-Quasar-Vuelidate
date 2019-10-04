![titulo](/docs/titulo.jpg)

# Validated Form (form-quasar-vuelidate)

Simple example of a Quasar form with Vuelidate plugin. 

## Technologies
- [Quasar Framework](https://quasar.dev)
- [Vuelidate Plugin](https://vuelidate.netlify.com/#sub-installation)

## How to run this project

### Install NPM dependencies
```bash
npm install
```

### Run the app
```bash
quasar dev
```
### Access the URL
```bash
http://localhost:8080
```

## Exploring the interface

First page containing the empty fields.

![quasar01](/docs/quasar01.JPG)

Detecting an invalid e-mail address.

![quasar02](/docs/quasar02.JPG)

Validating the password's minimum length.

![quasar03](/docs/quasar03.JPG)

All the form's conditions are valid.

![quasa04](/docs/quasar04.JPG)

Showing the form data in the next page.

![quasar05](/docs/quasar05.JPG)

## Explaining the code

Importing Vue and the Vuelidate plugin to register it.

![code02](/docs/code02.JPG)

Importing the Vuelidate features to validate the form fields.

![code01](/docs/code01.JPG)

Detecting if any condition from the email input is invalid.

![code03](/docs/code03.JPG)

Detecting if any condition from the password input is invalid.

![code04](/docs/code04.JPG)

If the form presents any invalid condition, the button will be disabled.

![code05](/docs/code05.JPG)
