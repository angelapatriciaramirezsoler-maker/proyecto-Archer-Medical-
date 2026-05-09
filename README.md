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

-- Operadores lógicos
SELECT * FROM Inventario WHERE Total_Hora > 50 AND Total_Hora <= 100;
