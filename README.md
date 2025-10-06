# prct03-AyD-BDD

## Modelo entidad/relación. Viveros Tajinaste S.A.

![](viveros.png)

---

# FALTA VIVEROS ZONAS, PLUS 3
### **Cliente**

Representa a las personas o empresas que realizan pedidos a la empresa Tajinaste S.A.

* **Cod_cli** *(PK, entero)* → Identificador único del cliente.
  Ej: `C001`, `C045`.
* **Nombre** *(texto)* → Nombre completo.
  Ej: `María López`.
* **Dirección** *(texto)* → Domicilio.
  Ej: `Av. El Rosario 15, Santa Cruz`.
* **Teléfono** *(texto)* → Número de contacto.
  Ej: `+34 5555555555`.
* **Correo** *(texto)* → Correo electrónico del cliente.
  Ej: `maria@correo.com`.

---

### **Empleado**

Personal encargado de atender a los clientes y registrar los pedidos.

* **Cod_emp** *(PK, entero)* → Identificador del empleado.
  Ej: `E001`.
* **Nombre** *(texto)* → Nombre del empleado.
  Ej: `Carlos Pérez`.
* **DNI** *(texto)* → DNI del empleado.
  Ej: `55555555`.
* **Teléfono** *(texto)* → Contacto directo.
  Ej: `+34 5555555554`.


---

### **Producto**

Artículos y plantas que el vivero ofrece a la venta.

* **Cod_prod** *(PK, entero)* → Identificador único del producto.
  Ej: `PR001`, `PL020`.
* **Nombre** *(texto)* → Nombre del producto.
  Ej: `Ficus`, `Maceta de barro`, `Abono líquido`.
* **Tipo** *(texto)* → Categoría general.
  Ej: `Planta`, `Decoración`, `Jardinería`.
* **Precio** *(decimal)* → Precio unitario del producto.
  Ej: `15.90`.
* **Stock** *(entero)* → Cantidad disponible en almacén.
  Ej: `120`.

---

### **Pedido**

Pedidos realizados por los clientes y gestionados por los empleados.

* **Cod_ped** *(PK, entero)* → Identificador del pedido.
  Ej: `PED001`.
* **Fecha_ped** *(fecha)* → Fecha de emisión del pedido.
  Ej: `2025-09-25`.
* **Cod_cli** *(FK)* → Cliente que realiza el pedido.
* **Cod_emp** *(FK)* → Empleado que atiende el pedido.
* **Total** *(decimal)* → Importe total del pedido.


---




# FALTA VIVEROS ZONAS Y PLUS 4

## **Relaciones**

### **Realiza (Cliente – Pedido)**

* Un cliente → puede realizar 1..N pedidos.
* Un pedido → pertenece a 1 cliente.


---

### **Atiende (Empleado – Pedido)**

* Un empleado → puede gestionar 0..N pedidos.
* Un pedido → es atendido por 1 empleado.


---

### **Contiene (Pedido – Producto)**

(Relación representada por *Detalle_pedido*)

* Un pedido → puede incluir 1..N productos.
* Un producto → puede estar en 0..N pedidos.



---

## **Restricciones semánticas**

* Todo **pedido** debe estar asociado a un cliente y un empleado.
* El **stock** no puede ser negativo.
* Las **unidades** vendidas no pueden superar el **stock**
* Los **precio** y **coste_final** deben ser valores positivos.

---


