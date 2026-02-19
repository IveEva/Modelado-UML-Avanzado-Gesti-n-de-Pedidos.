## Modelado-UML-Avanzado-Gesti-n-de-Pedidos.

```mermaid
classDiagram
    class Cliente {
        -String id
        -String nombre
        -String email
        +realizarPedido()
    }

    class Pedido {
        -String id
        -LocalDate fecha
        -EstadoPedido estado
        +agregarLinea(producto: Producto, cantidad: int)
        +calcularTotal() Double
    }

    class LineaPedido {
        -int cantidad
        -Double subtotal
        +calcularSubtotal()
    }

    class Producto {
        -String nombre
        -Double precio
    }

    <<enumeration>> EstadoPedido
    EstadoPedido : PENDIENTE
    EstadoPedido : ENTREGADO

    %% Relaciones
    Cliente "1" --> "0..*" Pedido : historial (asociación)
    Pedido "1" *-- "1..*" LineaPedido : compuesto por (composición)
    LineaPedido "0..*" o-- "1" Producto : referencia (agregación)
    Pedido ..> EstadoPedido : usa
```
