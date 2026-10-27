# Práctica 1: Clean Code y Refactorización

## 1. Objetivo

Identificar problemas de legibilidad y mantenibilidad en un fragmento de JavaScript y aplicar técnicas de refactorización sin alterar su comportamiento esperado.

## 2. Código original

El siguiente ejemplo representa una implementación inicial del cálculo de una venta.

```javascript
function venta(p, c, tipo, cliente) {
  let t = p * c;
  if (tipo === "VIP") {
    t = t - t * 0.15;
  } else if (tipo === "REGULAR") {
    t = t - t * 0.05;
  } else {
    t = t;
  }
  if (cliente !== null && cliente !== undefined) {
    console.log("Cliente: " + cliente);
  }
  console.log("Total: " + t);
  return t;
}
```

## 3. Code smells identificados

### 3.1. Poor Naming

Los nombres `p`, `c`, `t` y `tipo` no explican claramente el propósito de cada variable o parámetro.

**Mejora propuesta:** utilizar nombres descriptivos como `precio`, `cantidad`, `total` y `tipoCliente`.

### 3.2. Long Parameter List

La función recibe cuatro parámetros, algunos de los cuales podrían agruparse si el sistema creciera.

**Mejora propuesta:** para este ejemplo pequeño, priorizar nombres descriptivos. Si aumentaran los datos relacionados, podrían agruparse en un objeto.

### 3.3. Duplicated Conditional Logic

La estructura condicional mezcla la selección del descuento con el cálculo del total. Si las reglas crecieran, su mantenimiento sería más complicado.

**Mejora propuesta:** separar la obtención del descuento del cálculo de la venta.

### 3.4. Redundant Else

La instrucción `else` asigna `t = t`, operación que no cambia el valor.

**Mejora propuesta:** eliminar la asignación innecesaria.

## 4. Código refactorizado

```javascript
function obtenerDescuento(tipoCliente) {
  if (tipoCliente === "VIP") return 0.15;
  if (tipoCliente === "REGULAR") return 0.05;
  return 0;
}

function calcularVenta(precio, cantidad, tipoCliente, cliente) {
  const subtotal = precio * cantidad;
  const descuento = obtenerDescuento(tipoCliente);
  const total = subtotal * (1 - descuento);

  if (cliente != null) {
    console.log(`Cliente: ${cliente}`);
  }

  console.log(`Total: ${total}`);
  return total;
}
```

## 5. Mejoras realizadas

* Se reemplazaron los nombres ambiguos por nombres descriptivos.
* Se extrajo la lógica de selección del descuento a una función independiente.
* Se eliminó una asignación redundante.
* Se utilizó una plantilla de texto para mejorar la legibilidad.
* Se mantuvieron las tasas de descuento y el comportamiento de cálculo para los casos contemplados.

## 6. Verificación

Para comprobar el cálculo, se pueden utilizar estos casos:

| Precio | Cantidad | Tipo de cliente | Total esperado |
| -----: | -------: | --------------- | -------------: |
|    100 |        2 | VIP             |            170 |
|    100 |        2 | REGULAR         |            190 |
|    100 |        2 | Otro            |            200 |

Los resultados esperados corresponden a los descuentos del 15 %, 5 % y 0 %, respectivamente.

## 7. Conclusión

La refactorización permite comprender mejor las responsabilidades de cada función y facilita el mantenimiento de las reglas de descuento. Antes de considerar terminado el cambio, es necesario ejecutar las pruebas y comprobar que los resultados coincidan con los esperados.
