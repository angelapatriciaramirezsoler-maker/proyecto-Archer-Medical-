# 📦 Proyecto Archer Medical

Este repositorio contiene el sistema de gestión con **Node.js**, **Angular** y **MongoDB Atlas**.  
Incluye documentación técnica, diagramas y scripts SQL.

---

## 📂 Enlaces de Carpetas del Proyecto

- [Cliente Angular](https://github.com/angelapatriciaramirezsoler-maker/proyecto-Archer-Medical-/tree/main/cliente-angular)
- [Servidor Node.js](https://github.com/angelapatriciaramirezsoler-maker/proyecto-Archer-Medical-/tree/main/server)
- [Rutas API](https://github.com/angelapatriciaramirezsoler-maker/proyecto-Archer-Medical-/tree/main/server/routes)
- [Modelos Mongoose](https://github.com/angelapatriciaramirezsoler-maker/proyecto-Archer-Medical-/tree/main/server/models)
- [Base de Datos](https://github.com/angelapatriciaramirezsoler-maker/proyecto-Archer-Medical-/tree/main/server/database)
// models/empleado.js
const mongoose = require("mongoose");

const empleadoSchema = new mongoose.Schema({
  name: String,
  position: String,
  office: String,
  salary: Number
});

module.exports = mongoose.model("Empleado", empleadoSchema);

---

## 🗄️ Scripts Base de Datos (SQL)

Ejemplos de consultas DML y operadores:

```sql
-- Selección de tablas principales
SELECT * FROM operario;
SELECT * FROM inventario;
SELECT * FROM informes;
SELECT * FROM usuario;
SELECT * FROM tipo_de_farmacias;

-- Dependencia transitiva con JOIN
SELECT im.Id_Casilla, im.Nombre_Casilla, inv.IdInventario, inv.Nombre_Inventario, inv.Total_Hora
FROM inventario_medicamentos AS im
INNER JOIN inventario AS inv ON im.Id_Casilla = inv.IdInventario
WHERE inv.Total_Hora > 5;
// routes/empleado.route.js
const express = require("express");
const router = express.Router();
const Empleado = require("../models/empleado");

router.post("/", async (req, res) => {
  const nuevo = new Empleado(req.body);
  await nuevo.save();
  res.json(nuevo);
});

router.get("/", async (req, res) => {
  const empleados = await Empleado.find();
  res.json(empleados);
});

module.exports = router;
// index.js
const express = require("express");
const cors = require("cors");
const morgan = require("morgan");
const empleadoRoutes = require("./routes/empleado.route");

const app = express();
app.use(cors());
app.use(morgan("dev"));
app.use(express.json());

app.use("/api/empleados", empleadoRoutes);

app.listen(3000, () => console.log("Servidor corriendo en puerto 3000"));
proyecto-Archer-Medical-/
│── cliente-angular/
│── server/
│   ├── routes/
│   ├── models/
│   ├── database/
│   └── index.js
│── README.md

---

✅ Con este README cumples exactamente con lo que te piden:  
- Enlaces de GitHub de las carpetas  
- Scripts de base de datos  
- Scripts de codificación de módulos  

---

¿Quieres que te prepare el archivo `README.md` ya listo para **copiar y pegar directamente en tu repositorio** sin que tengas que editar nada más?
-- Operadores lógicos
SELECT * FROM Inventario WHERE Total_Hora > 50 AND Total_Hora <= 100;
