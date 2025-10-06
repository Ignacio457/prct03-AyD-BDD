# prct03-AyD-BDD

## Modelo entidad/relación. Viveros Tajinaste S.A.

![](ADBD3.png)

---
### **Vivero**

Centro físico donde se cultivan y almacenan productos y plantas.

* **Cod_vivero** *(PK, entero)* → Identificador único del vivero.
  Ej: `V01`, `V02`.
* **Nombre** *(texto)* → Nombre del vivero.
  Ej: `Vivero Norte`, `Vivero Sur`.
* **Longitud / Latitud** *(decimal)* → Coordenadas geográficas.
  Ej: `(-16.25, 28.48)`.

---

### **Zona**

Áreas específicas dentro de cada vivero donde se agrupan productos.

* **Cod_zona** *(PK, entero)* → Identificador de la zona.
  Ej: `Z01`, `Z05`.
* **Nombre** *(texto)* → Descripción o nombre de la zona.
  Ej: `Zona tropical`, `Zona almacén`.
* **Longitud / Latitud** *(decimal)* → Coordenadas de ubicación.
  Ej: `(-16.26, 28.49)`.

---

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

### **Tajinaste Plus**

Programa de fidelización para clientes frecuentes.

* **Cod_plus** *(PK, entero)* → Identificador único del programa Plus.
  Ej: `PL001`.
* **Cod_cliente** *(FK)* → Cliente asociado.
* **Fecha_ingreso** *(fecha)* → Fecha de adhesión al programa.
  Ej: `2025-01-15`.
* **Bonificación** *(decimal)* → Puntos o euros acumulados.
  Ej: `12.50`.

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


## **Relaciones**


### **Contiene (Vivero – Zona)**

* Un vivero → contiene 1..N zonas.
* Una zona → pertenece a 1 vivero.
  Ejemplo: *Vivero Sur* contiene las zonas *Almacén* y *Exteriores*.

---

### **Tiene (Zona – Producto)**

* Una zona → puede tener 0..N productos.
* Un producto → puede estar en 1..N zonas.
  Ejemplo: La *Zona Tropical* tiene los productos *Ficus* y *Helecho*.

---

### **Asignado (Empleado – Zona)**

* Un empleado → puede estar asignado a 1 zonas.
* Una zona → puede tener 1..N empleados.
  Atributos: *fecha_inicio*, *fecha_fin*, *puesto*.
  Ejemplo: *Carlos Pérez* trabaja en la *Zona Exterior* desde `2025-02-01`.

---

### **Tiene (Cliente – Tajinaste Plus)**

* Un cliente → puede tener 0..1 Tajinaste Plus.
* Un Tajinaste Plus → pertenece a 1 cliente.
  Ejemplo: *María López* posee un programa *Tajinaste Plus* con bonificación de 20 €.


### **Realiza (Tajinaste PLus – Pedido)**

* Un cliente plus → puede realizar 1..N pedidos.
* Un pedido → pertenece a 1 cliente.


---

### **Gestionado (Empleado – Pedido)**

* Un empleado → puede gestionar 0..N pedidos.
* Un pedido → es gestionado por 1 empleado.


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


