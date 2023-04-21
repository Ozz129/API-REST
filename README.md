# API-REST

// importamos express para levantar el servidor
const express = require('express');
const app = express();
const comentariosRouter = require('./apiRouters')

app.use(express.json())
app.use('/comentarios', comentariosRouter);

// localhost:3000/comentarios/

// Agregamos rutas
app.get('/users/:id', (req, res) => {
    const userId = req.params.id;
    // Obtener información del usuario con el ID proporcionado
    res.send(`Información del usuario ${userId}`);
});

app.post('/users', (req, res) => {
    // Crear un nuevo usuario con la información proporcionada en la solicitud
    res.send({
        msg: 'Usuario creado',
        data: req.body
    });
});
  

const port = 3000;

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});


----------- ROUTER

const express = require('express');
const router = express.Router();

// Ruta para obtener todos los comentarios
router.get('/', (req, res) => {
  res.send('Obteniendo todos los comentarios');
});

// Ruta para obtener un comentario por ID
router.get('/:id', (req, res) => {
  res.send(`Obteniendo comentario con ID ${req.params.id}`);
});

// Ruta para crear un comentario
router.post('/', (req, res) => {
  res.send('Creando un nuevo comentario');
});

// Ruta para actualizar un comentario por ID
router.put('/:id', (req, res) => {
  res.send(`Actualizando comentario con ID ${req.params.id}`);
});

// Ruta para eliminar un comentario por ID
router.delete('/:id', (req, res) => {
  res.send(`Eliminando comentario con ID ${req.params.id}`);
});

module.exports = router;
