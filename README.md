const express = require('express');
const cors = require('cors');

const app = express();
const PORT = process.env.PORT || 3000;

// Middleware
app.use(cors());
app.use(express.json());

// Rutas
app.get('/', (req, res) => {
    res.send('¡Bienvenido a mi página web!');
});

// Ejemplo de API REST
let items = [
    { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' }
];

// Obtener todos los items
app.get('/api/items', (req, res) => {
    res.json(items);
});

// Agregar un nuevo item
app.post('/api/items', (req, res) => {
    const newItem = {
        id: items.length + 1,
        name: req.body.name
    };
    items.push(newItem);
    res.status(201).json(newItem);
});

// Iniciar el servidor
app.listen(PORT, () => {
    console.log(`Servidor corriendo en http://localhost:${PORT}`);
});
