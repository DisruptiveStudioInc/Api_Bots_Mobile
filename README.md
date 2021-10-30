<h1 align="center">Api ibot</h1>


<br>

## :dart: Acerca de ##

API Para acceso a los datos para app movil

## :sparkles: Caracteristicas ##

:heavy_check_mark: Transacciones 1;\
:heavy_check_mark: Login por QR;\
:heavy_check_mark: Estadisticas;\
:heavy_check_mark: Bots;

## :rocket: Tecnologias ##

Las siguientes tecnologias se utilizaron en el proyecto:

- [Node.js](https://nodejs.org/en/)
- [TypeScript](https://www.typescriptlang.org/)

## :white_check_mark: Requerimentos ##

Antes de iniciar :checkered_flag:, necesitas tener [Git](https://git-scm.com) y [Node](https://nodejs.org/en/) instalados.

## :checkered_flag: Iniciar ##

```bash
# Clone this project
$ git clone https://github.com/edgar017/apiibot

# Access
$ cd apiibot

# Install dependencies
$ npm install

# Run the project
$ npm start

# The server will initialize in the <http://localhost:3000>
```

# Metodos #

## EndPoint ##

- Produccion: 
- - https://mobile.bot-control.app
- Test: 
- - Pendiente



## Login ##

Para hacer login en la API, es necesario enviar el Codigo de cliente, con ello, podrás obtener un Token JWT para autenticarte en los demás metodos, a continuacion se detallan los parametros para obtener el token.

- Ruta:
- - /Auth/Login

- Metodo: 
- - POST

- Datos: 
- - Codigo: El codigo unico del cliente, se utiliza para identificar a cada cliente de manera independiente.

```bash
  curl -XPOST -H "Content-type: application/json" -d '{ "Codigo": "xxx"}' 'https://mobile.bot-control.app/Auth/Login'
```

- Respuesta
- - Datos: 
- - - isError: true | false
- - - token: Token JWT

```json
  {
    "isError": false,
    "token": "ksqwertyuhgfdssdfgtresxcvbhytredghtres$"
  }
```

## Transacciones ##

El sistema muestra las ultimas 200 operaciones de acuerdo al estado seleccionado.

- Ruta:
- - /Transacciones/:Estado

- Metodo:
- - GET 


- Estados:
 - - Pendientes
 - - - Obener las ultimas 200 operaciones pendientes del usuario ordenado de mayor a menor antiguedad.
 - - Canceladas
  - - - Obtener las ultimas 200 operaciones canceladas del usuario ordenadas de mayor a menor.
  - - Completas
  - - - Obtener las ultimas 200 operaciones completadas del usuario ordenadas de mayor a menor.

  ** Nota: El query url es el estado escrito capitalizando la primera, ejemplo: /Transacciones/Pendientes

### Metodo en curl: ###

```bash
  curl -XGET -H 'auth-token: TokenGeneradoAnteriormente' -H "Content-type: application/json"  'https://mobile.bot-control.app/Transacciones/Pendientes'
```

- Respuesta
- - Datos: 
- - - isError: true | false
- - - data: Transacciones

```json
  {
    "isError": false,
    "data": [
        {
            "Fase": 4,
            "Codigo": "NDBQ_sQpx4CkTdxIAdk",
            "Token": "DOT/BTC",
            "Monto": "22.83846748313069"
        },
        {
            "Fase": 4,
            "Codigo": "9Q-ENjK0n5ghKP9dyS9",
            "Token": "SOL/BTC",
            "Monto": "6.526122614859372"
        },
        {
            "Fase": 4,
            "Codigo": "zzN8YaX3FTe6uc7H5_U",
            "Token": "BNB/BTC",
            "Monto": "2.374173183463532"
        },
        {
            "Fase": 4,
            "Codigo": "ZACPsF8DVQLinkwHJf",
            "Token": "DOT/BTC",
            "Monto": "27.945673677440674"
        },
        {
            "Fase": 4,
            "Codigo": "nYUsCbVJ7cZfsdNxmizC6sU",
            "Token": "SOL/BTC",
            "Monto": "6.628502383666462"
        },
        {
            "Fase": 4,
            "Codigo": "97YkyvjjAgDPdQG4ddseDsh1-",
            "Token": "SOL/BTC",
            "Monto": "6.626136531096475"
        }
  }
```

*** Nota: Todos los metodos de operaciones devolverán la misma estructura
  