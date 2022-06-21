create database COMERCIALIZADORA_JULIO;

use COMERCIALIZADORA_JULIO;

CREATE TABLE `CATEGORIA_PRODUCTOS` (
  `id` int(11) NOT NULL,
  `categoria` varchar(20) NOT NULL
) ENGINE = InnoDB DEFAULT CHARSET = utf8mb4;

INSERT INTO
  `CATEGORIA_PRODUCTOS` (`id`, `categoria`)
VALUES
  (1, 'cristaleria'),
  (3, 'cubiertos'),
  (4, 'manteles'),
  (6, 'reposteria'),
  (5, 'servilletas'),
  (2, 'vajilllas');

CREATE TABLE `CLIENTES` (
  `n_cliente` int(11) NOT NULL,
  `nombre` varchar(30) NOT NULL,
  `direccion` text NOT NULL,
  `correo` varchar(50) NOT NULL,
  `telefono` char(10) NOT NULL,
  `contacto` varchar(30) DEFAULT NULL
) ENGINE = InnoDB DEFAULT CHARSET = utf8mb4;

INSERT INTO
  `CLIENTES` (
    `n_cliente`,
    `nombre`,
    `direccion`,
    `correo`,
    `telefono`,
    `contacto`
  )
VALUES
  (
    1,
    'Julio Cesar Tovar',
    'GALICIA 48 27277 VILLAS DE LAS PERLAS',
    'caesarnetyet@gmail.com',
    '8135164652',
    NULL
  ),
  (
    2,
    'Glenda Archuleta Betancourt',
    '1464 Terra Street\r\nSilverdale, WA 98383',
    'GlendaArchuletaBetancourt@armyspy.com',
    '3603088252',
    NULL
  ),
  (
    3,
    'Fito Beltrán Noriega',
    '1618 Geneva Street\r\nMineola, NY 11501',
    'FitoBeltranNoriega@armyspy.com',
    '9175094144',
    NULL
  ),
  (
    4,
    'Vero Ortega Díaz',
    '3825 Brannon Street\r\nAnaheim, CA 92801',
    'VeroOrtegaDiaz@teleworm.us',
    '2132554400',
    NULL
  ),
  (
    5,
    'Edelmar Alva Bonilla',
    '1049 Counts Lane\r\nBerea, KY 40403',
    'EdelmarAlvaBonilla@jourrapide.com',
    '8599856968',
    NULL
  ),
  (
    6,
    'Leoncio Carmona Collado',
    '760 Goldleaf Lane\r\nBranchburg, NJ 08817',
    'LeoncioCarmonaCollado@rhyta.com',
    '2016029842',
    NULL
  ),
  (
    7,
    'Kemal Canales Velez',
    '1861 Morgan Street\r\nTallahassee, FL 32301',
    'KemalCanalesVelez@rhyta.com',
    '8505286678',
    NULL
  ),
  (
    8,
    'Aurea Centeno Alcantar',
    '3783 Goodwin Avenue\r\nSpokane, WA 99201',
    'AureaCentenoAlcantar@armyspy.com',
    '5093521833',
    NULL
  ),
  (
    9,
    'Aurea Centeno Alcantar',
    '3783 Goodwin Avenue\r\nSpokane, WA 99201\r\n',
    'ToscanaSaenzToro@dayrep.com',
    '6623902003',
    NULL
  ),
  (
    10,
    'Audomaro Carreón Alonzo',
    '69 Pine Garden Lane\r\nNorcross, GA 30071\r\n',
    'AudomaroCarreonAlonzo@teleworm.us',
    '7707581346',
    NULL
  );

CREATE TABLE `DETALLE_ORDEN_COMPRA` (
  `orden_compra` int(11) NOT NULL,
  `producto` int(11) NOT NULL,
  `cantidad` int(10) NOT NULL,
  `precio_compra` double NOT NULL
) ENGINE = InnoDB DEFAULT CHARSET = utf8mb4;

INSERT INTO
  `DETALLE_ORDEN_COMPRA` (
    `orden_compra`,
    `producto`,
    `cantidad`,
    `precio_compra`
  )
VALUES
  (1, 8, 10, 120),
  (2, 6, 2, 15),
  (6, 7, 20, 30),
  (8, 4, 2, 32.5),
  (3, 9, 40, 10),
  (4, 5, 5, 42),
  (9, 10, 5, 320),
  (7, 9, 50, 8),
  (3, 2, 3, 1500),
  (8, 1, 20, 25);

CREATE TABLE `DETALLE_ORDEN_VENTA` (
  `orden_venta` int(11) DEFAULT NULL,
  `producto` int(11) NOT NULL,
  `cantidad` int(10) NOT NULL
) ENGINE = InnoDB DEFAULT CHARSET = utf8mb4;

INSERT INTO
  `DETALLE_ORDEN_VENTA` (`orden_venta`, `producto`, `cantidad`)
VALUES
  (12, 2, 10),
  (14, 7, 3),
  (10, 6, 12),
  (17, 5, 5),
  (15, 1, 10),
  (12, 6, 4),
  (2, 9, 12),
  (14, 3, 4),
  (10, 10, 2),
  (16, 10, 23);

CREATE TABLE `ORDEN_COMPRA` (
  `reg` int(11) NOT NULL,
  `fecha` datetime DEFAULT NULL,
  `proveedor` int(11) NOT NULL
) ENGINE = InnoDB DEFAULT CHARSET = utf8mb4;

INSERT INTO
  `ORDEN_COMPRA` (`reg`, `fecha`, `proveedor`)
VALUES
  (1, '2022-05-16 10:35:02', 2),
  (2, '2022-05-16 10:35:02', 4),
  (3, '2022-05-16 10:37:20', 9),
  (4, '2022-05-16 10:37:20', 1),
  (5, '2022-05-16 10:37:20', 8),
  (6, '2022-05-16 10:37:20', 7),
  (7, '2022-05-16 10:37:20', 9),
  (8, '2022-05-16 10:37:20', 3),
  (9, '2022-05-16 10:37:20', 8),
  (10, '2022-05-16 10:37:20', 1);

CREATE TABLE `ORDEN_VENTA` (
  `reg` int(11) NOT NULL,
  `fecha` datetime DEFAULT NULL,
  `cliente` int(11) NOT NULL,
  `forma_pago` varchar(20) NOT NULL CHECK (
    `forma_pago` = 'debito'
    or `forma_pago` = 'efectivo'
    or `forma_pago` = 'credito'
  )
) ENGINE = InnoDB DEFAULT CHARSET = utf8mb4;

INSERT INTO
  `ORDEN_VENTA` (`reg`, `fecha`, `cliente`, `forma_pago`)
VALUES
  (1, '2022-05-16 10:38:28', 1, 'credito'),
  (2, '2022-05-16 10:38:28', 8, 'debito'),
  (10, '2022-05-16 10:43:18', 1, 'credito'),
  (11, '2022-05-16 10:43:18', 7, 'debito'),
  (12, '2022-05-16 10:43:18', 2, 'efectivo'),
  (13, '2022-05-16 10:43:18', 6, 'credito'),
  (14, '2022-05-16 10:43:18', 8, 'debito'),
  (15, '2022-05-16 10:43:18', 3, 'efectivo'),
  (16, '2022-05-16 10:43:18', 9, 'credito'),
  (17, '2022-05-16 10:43:18', 4, 'efectivo');

CREATE TABLE `PRODUCTOS` (
  `codigo` int(11) NOT NULL,
  `nombre` varchar(40) NOT NULL,
  `descripcion` text NOT NULL,
  `existencias` int(11) NOT NULL,
  `precio_venta` double NOT NULL,
  `categoria` int(11) NOT NULL
) ENGINE = InnoDB DEFAULT CHARSET = utf8mb4;

INSERT INTO
  `PRODUCTOS` (
    `codigo`,
    `nombre`,
    `descripcion`,
    `existencias`,
    `precio_venta`,
    `categoria`
  )
VALUES
  (
    1,
    'Vaso de vidrio',
    'Un vaso de vidrio creado para el consumo de liquidos',
    999,
    31.99,
    1
  ),
  (
    2,
    'Cristal para mesa',
    'Cristal para mesa redonda de 100 x 100 cm',
    995,
    2500,
    1
  ),
  (
    3,
    'tenedores de plastico',
    'paquete de 20 tenedores de plastico marca patito',
    999,
    18.99,
    3
  ),
  (
    4,
    'Molde para pastel',
    'Molde para pastel circular 50 x 50 cm',
    992,
    51.5,
    6
  ),
  (
    5,
    'vasos de plastico',
    'paquete de 100 vasos de plastico que soportan 500 ml',
    999,
    48.25,
    3
  ),
  (
    6,
    'vajilla de barro',
    'vajilla de barro para acomodar cosas',
    999,
    24.5,
    2
  ),
  (
    7,
    'servilletas de papel',
    'paquete de 500 servilletas de papel',
    650,
    41.75,
    5
  ),
  (
    8,
    'Mantel de spiderman',
    'Mantel de spiderman para una mesa grande de 500 x 200 cm ',
    239,
    400,
    4
  ),
  (
    9,
    'tenedores de plastico',
    'Paquete de 100 tenedores de plastico',
    341,
    20,
    3
  ),
  (
    10,
    'platos de vidrio',
    'paquete con 50 platos de vidrio para cenas elegantes',
    100,
    450,
    1
  );

-- --------------------------------------------------------
--
-- Estructura de tabla para la tabla `PROVEEDORES`
--
CREATE TABLE `PROVEEDORES` (
  `clave` int(11) NOT NULL,
  `nombre` varchar(40) NOT NULL,
  `direccion` text NOT NULL,
  `telefono` char(10) NOT NULL
) ENGINE = InnoDB DEFAULT CHARSET = utf8mb4;

--
-- Volcado de datos para la tabla `PROVEEDORES`
--
INSERT INTO
  `PROVEEDORES` (`clave`, `nombre`, `direccion`, `telefono`)
VALUES
  (
    1,
    'Patito',
    '218 Laurel Lane\r\nTerminal, TX 79703',
    '4324999660'
  ),
  (
    2,
    'Extranjero',
    '281 Cecil Street\r\nChicago, IL 60606\r\n',
    '3122148791'
  ),
  (
    3,
    'Carroll-Miller',
    '3637 Adonais Way\r\nAtlanta, GA 30308\r\n',
    '6783982266'
  ),
  (
    4,
    'Gorczany, Hermiston and Leffler	',
    '3637 Adonais Way\r\nAtlanta, GA 30308',
    '6783982266'
  ),
  (
    5,
    'Little-Legros',
    '4188 Cherry Ridge Drive\r\nRoseville, MI 48066',
    '5862943054'
  ),
  (
    6,
    'Mueller, Bernier and Ward	',
    '4188 Cherry Ridge Drive\r\nRoseville, MI 48066',
    '5862943054'
  ),
  (
    7,
    'Carter Ltd',
    '4188 Cherry Ridge Drive\r\nRoseville, MI 48066\r\n',
    '5862943054'
  ),
  (
    8,
    'Skiles-Blick	',
    '3427 Cook Hill Road\r\nStratford, CT 06497',
    '2035029857'
  ),
  (
    9,
    'Langworth, Schultz and Daniel',
    '3340 Charter Street\r\nOlathe, KS 66061',
    '9137684144'
  ),
  (
    10,
    'Farrell, Keeling and DuBuque',
    '3766 Pringle Drive\r\nChicago, IL 60601',
    '3123747955'
  );

--
-- Índices para tablas volcadas
--
--
-- Indices de la tabla `CATEGORIA_PRODUCTOS`
--
ALTER TABLE
  `CATEGORIA_PRODUCTOS`
ADD
  PRIMARY KEY (`id`),
ADD
  UNIQUE KEY `categoria` (`categoria`);

--
-- Indices de la tabla `CLIENTES`
--
ALTER TABLE
  `CLIENTES`
ADD
  PRIMARY KEY (`n_cliente`),
ADD
  UNIQUE KEY `correo` (`correo`);

--
-- Indices de la tabla `DETALLE_ORDEN_COMPRA`
--
ALTER TABLE
  `DETALLE_ORDEN_COMPRA`
ADD
  KEY `orden_compra` (`orden_compra`),
ADD
  KEY `producto` (`producto`);

--
-- Indices de la tabla `DETALLE_ORDEN_VENTA`
--
ALTER TABLE
  `DETALLE_ORDEN_VENTA`
ADD
  KEY `orden_venta` (`orden_venta`),
ADD
  KEY `producto` (`producto`);

--
-- Indices de la tabla `ORDEN_COMPRA`
--
ALTER TABLE
  `ORDEN_COMPRA`
ADD
  PRIMARY KEY (`reg`),
ADD
  KEY `proveedor` (`proveedor`);

--
-- Indices de la tabla `ORDEN_VENTA`
--
ALTER TABLE
  `ORDEN_VENTA`
ADD
  PRIMARY KEY (`reg`),
ADD
  KEY `cliente` (`cliente`);

--
-- Indices de la tabla `PRODUCTOS`
--
ALTER TABLE
  `PRODUCTOS`
ADD
  PRIMARY KEY (`codigo`),
ADD
  KEY `categoria` (`categoria`);

--
-- Indices de la tabla `PROVEEDORES`
--
ALTER TABLE
  `PROVEEDORES`
ADD
  PRIMARY KEY (`clave`),
ADD
  UNIQUE KEY `nombre` (`nombre`);

--
-- AUTO_INCREMENT de las tablas volcadas
--
--
-- AUTO_INCREMENT de la tabla `CATEGORIA_PRODUCTOS`
--
ALTER TABLE
  `CATEGORIA_PRODUCTOS`
MODIFY
  `id` int(11) NOT NULL AUTO_INCREMENT,
  AUTO_INCREMENT = 7;

--
-- AUTO_INCREMENT de la tabla `CLIENTES`
--
ALTER TABLE
  `CLIENTES`
MODIFY
  `n_cliente` int(11) NOT NULL AUTO_INCREMENT,
  AUTO_INCREMENT = 11;

--
-- AUTO_INCREMENT de la tabla `ORDEN_COMPRA`
--
ALTER TABLE
  `ORDEN_COMPRA`
MODIFY
  `reg` int(11) NOT NULL AUTO_INCREMENT,
  AUTO_INCREMENT = 11;

--
-- AUTO_INCREMENT de la tabla `ORDEN_VENTA`
--
ALTER TABLE
  `ORDEN_VENTA`
MODIFY
  `reg` int(11) NOT NULL AUTO_INCREMENT,
  AUTO_INCREMENT = 18;

--
-- AUTO_INCREMENT de la tabla `PRODUCTOS`
--
ALTER TABLE
  `PRODUCTOS`
MODIFY
  `codigo` int(11) NOT NULL AUTO_INCREMENT,
  AUTO_INCREMENT = 11;

--
-- AUTO_INCREMENT de la tabla `PROVEEDORES`
--
ALTER TABLE
  `PROVEEDORES`
MODIFY
  `clave` int(11) NOT NULL AUTO_INCREMENT,
  AUTO_INCREMENT = 11;

--
-- Restricciones para tablas volcadas
--
--
-- Filtros para la tabla `DETALLE_ORDEN_COMPRA`
--
ALTER TABLE
  `DETALLE_ORDEN_COMPRA`
ADD
  CONSTRAINT `detalle_orden_compra_ibfk_1` FOREIGN KEY (`orden_compra`) REFERENCES `ORDEN_COMPRA` (`reg`),
ADD
  CONSTRAINT `detalle_orden_compra_ibfk_2` FOREIGN KEY (`producto`) REFERENCES `PRODUCTOS` (`codigo`);

--
-- Filtros para la tabla `DETALLE_ORDEN_VENTA`
--
ALTER TABLE
  `DETALLE_ORDEN_VENTA`
ADD
  CONSTRAINT `detalle_orden_venta_ibfk_1` FOREIGN KEY (`orden_venta`) REFERENCES `ORDEN_VENTA` (`reg`),
ADD
  CONSTRAINT `detalle_orden_venta_ibfk_2` FOREIGN KEY (`producto`) REFERENCES `PRODUCTOS` (`codigo`);

--
-- Filtros para la tabla `ORDEN_COMPRA`
--
ALTER TABLE
  `ORDEN_COMPRA`
ADD
  CONSTRAINT `orden_compra_ibfk_1` FOREIGN KEY (`proveedor`) REFERENCES `PROVEEDORES` (`clave`);

--
-- Filtros para la tabla `ORDEN_VENTA`
--
ALTER TABLE
  `ORDEN_VENTA`
ADD
  CONSTRAINT `orden_venta_ibfk_1` FOREIGN KEY (`cliente`) REFERENCES `CLIENTES` (`n_cliente`);

--
-- Filtros para la tabla `PRODUCTOS`
--
ALTER TABLE
  `PRODUCTOS`
ADD
  CONSTRAINT `productos_ibfk_1` FOREIGN KEY (`categoria`) REFERENCES `CATEGORIA_PRODUCTOS` (`id`);

COMMIT;

/*C O N S U L T A S*/
/*Muestra los clientes y su contacto*/
select
  CLIENTES.nombre as Cliente,
  CLIENTES.contacto
from
  CLIENTES;

/*Muestra el numero de productos que compro cada cliente*/
SELECT
  CLIENTES.nombre as Cliente,
  PRODUCTOS.nombre as Producto,
  DETALLE_ORDEN_VENTA.cantidad as Cantidad
from
  CLIENTES
  INNER JOIN ORDEN_VENTA on ORDEN_VENTA.cliente = CLIENTES.n_cliente
  INNER JOIN DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.orden_venta = ORDEN_VENTA.reg
  INNER JOIN PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_VENTA.producto;

/*Muestra cuantos clientes pagaron con credito*/
SELECT
  ORDEN_VENTA.forma_pago as Forma_de_pago,
  COUNT(CLIENTES.n_cliente) as Numero_de_clientes
from
  ORDEN_VENTA
  INNER JOIN CLIENTES on CLIENTES.n_cliente = ORDEN_VENTA.cliente
WHERE
  ORDEN_VENTA.forma_pago = 'credito'
ORDER BY
  ORDEN_VENTA.forma_pago;

/*Muestra cada producto con su categoria*/
select
  PRODUCTOS.nombre as Producto,
  CATEGORIA_PRODUCTOS.categoria as Categoria
from
  PRODUCTOS
  join CATEGORIA_PRODUCTOS on PRODUCTOS.categoria = CATEGORIA_PRODUCTOS.id;

/*Muestra el cliente, la fecha y la forma de pago donde realizo su compra*/
select
  CLIENTES.nombre as Cliente,
  ORDEN_VENTA.fecha as Fecha,
  ORDEN_VENTA.forma_pago as Forma_de_pago
from
  CLIENTES
  join ORDEN_VENTA on ORDEN_VENTA.cliente = CLIENTES.n_cliente;

/*Muestra productos con existencias arriba de 500*/
select
  PRODUCTOS.nombre as Producto,
  PRODUCTOS.existencias
from
  PRODUCTOS
where
  PRODUCTOS.existencias > 500;

/*Muestra cuantos clientes han pagado con efectivo*/
SELECT
  ORDEN_VENTA.forma_pago as Forma_de_pago,
  COUNT(CLIENTES.n_cliente) as Numero_de_clientes
from
  ORDEN_VENTA
  INNER JOIN CLIENTES on CLIENTES.n_cliente = ORDEN_VENTA.cliente
WHERE
  ORDEN_VENTA.forma_pago = 'efectivo'
ORDER BY
  ORDEN_VENTA.forma_pago;

/*Selecciona cuantos productos vienen del extranjero*/
SELECT
  PROVEEDORES.nombre as Proveedores,
  COUNT(PRODUCTOS.codigo) AS Productos
from
  PROVEEDORES
  join ORDEN_COMPRA on PROVEEDORES.clave = ORDEN_COMPRA.proveedor
  join DETALLE_ORDEN_COMPRA on DETALLE_ORDEN_COMPRA.orden_compra = ORDEN_COMPRA.reg
  join PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_COMPRA.producto
where
  PROVEEDORES.nombre = 'Extranjero';

/*Selecciona los clientes que pagaron con debito*/
SELECT
  ORDEN_VENTA.forma_pago as Forma_de_pago,
  COUNT(CLIENTES.n_cliente) as Numero_de_clientes
from
  ORDEN_VENTA
  INNER JOIN CLIENTES on CLIENTES.n_cliente = ORDEN_VENTA.cliente
WHERE
  ORDEN_VENTA.forma_pago = 'debito'
ORDER BY
  ORDEN_VENTA.forma_pago;

/*Muestra el nombre y telefono de los proveedores con arriba de 3 productos*/
select
  PROVEEDORES.nombre as Nombre,
  PROVEEDORES.telefono
from
  PROVEEDORES
  JOIN ORDEN_COMPRA on ORDEN_COMPRA.proveedor = PROVEEDORES.clave
  join DETALLE_ORDEN_COMPRA on DETALLE_ORDEN_COMPRA.orden_compra = ORDEN_COMPRA.reg
where
  DETALLE_ORDEN_COMPRA.cantidad > 3;

/*Muestra los clientes y su telefono que hayan comprado por lo menos 5 productos*/
select
  CLIENTES.nombre,
  CLIENTES.telefono
from
  CLIENTES
  JOIN ORDEN_VENTA on ORDEN_VENTA.cliente = CLIENTES.n_cliente
  join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.orden_venta = ORDEN_VENTA.reg
where
  DETALLE_ORDEN_VENTA.cantidad > 5;

/*Muestra los productos y su precio*/
select
  PRODUCTOS.nombre as Producto,
  PRODUCTOS.precio_venta as Precio
from
  PRODUCTOS;

/*Muestra los productos que tengan un precio por arriba de 400 pesos*/
select
  PRODUCTOS.nombre as Producto,
  PRODUCTOS.precio_venta as Precio
from
  PRODUCTOS
where
  PRODUCTOS.precio_venta > 400;

/*Selecciona los clientes y su correo electronico*/
SELECT
  CLIENTES.nombre as Cliente,
  CLIENTES.correo
from
  CLIENTES;

/*Selecciona todos los clientes con su contacto*/
SELECT
  CLIENTES.nombre as Cliente,
  CLIENTES.contacto
from
  CLIENTES;

/*MOSTRAR EN QUE ORDENES DE VENTA SE VENDIO DETERMINADO PRODUCTO, EN QUE CANTIDAD, EL SUBTOTAL, IVA Y MONTO TOTAL OBTENIDO*/
SELECT
  ORDEN_VENTA.reg as Registro,
  PRODUCTOS.nombre as Producto,
  DETALLE_ORDEN_VENTA.cantidad as Cantidad,
  SUM(
    DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta
  ) as Subtotal,
  SUM(
    DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta *.16
  ) as IVA,
  SUM(
    (
      DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta *.16
    ) + (
      DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta
    )
  ) as TOTAL
from
  DETALLE_ORDEN_VENTA
  join PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_VENTA.producto
  join ORDEN_VENTA on ORDEN_VENTA.reg = DETALLE_ORDEN_VENTA.orden_venta
where
  PRODUCTOS.nombre = 'vasos de plastico';

/*Mostrar el monto de ventas al lado de la orden*/
SELECT
  ORDEN_VENTA.reg as ORDEN_VENTA,
  (
    DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta *.16
  ) + (
    DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta
  ) as TOTAL
from
  ORDEN_VENTA
  join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.orden_venta = ORDEN_VENTA.reg
  join PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_VENTA.producto;

/*Selecciona los 3 productos mas caros*/
SELECT
  PRODUCTOS.nombre,
  PRODUCTOS.precio_venta
from
  PRODUCTOS
order by
  PRODUCTOS.precio_venta desc
LIMIT
  3;

/*OBTEN LAS VENTAS TOTALES */
SELECT
  SUM(
    DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta
  ) as MONTO_TOTAL
from
  DETALLE_ORDEN_VENTA
  join ORDEN_VENTA on ORDEN_VENTA.reg = DETALLE_ORDEN_VENTA.orden_venta
  join PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_VENTA.producto
order by
  MONTO_TOTAL;

/*Calcular los montos de compra*/
SELECT
  ORDEN_COMPRA.reg,
  DETALLE_ORDEN_COMPRA.precio_compra * DETALLE_ORDEN_COMPRA.cantidad as TOTAL_COMPRA
from
  ORDEN_COMPRA
  join DETALLE_ORDEN_COMPRA on DETALLE_ORDEN_COMPRA.orden_compra = ORDEN_COMPRA.reg;

/*Selecciona todos los clientes que no hayan comprado*/
SELECT
  CLIENTES.nombre as Cliente
from
  CLIENTES
  LEFT JOIN ORDEN_VENTA on ORDEN_VENTA.cliente = CLIENTES.n_cliente
where
  ORDEN_VENTA.cliente is null;

/*OBTEN LA UTILIDAD*/
SELECT
  *,
  PRODUCTOS.precio_venta - DETALLE_ORDEN_COMPRA.precio_compra as UTILIDAD
from
  PRODUCTOS
  JOIN DETALLE_ORDEN_COMPRA ON DETALLE_ORDEN_COMPRA.producto = PRODUCTOS.codigo;

/*Obtener el producto mas caro con subconsulta*/
SELECT
  PRODUCTOS.nombre,
  PRODUCTOS.precio_venta as Producto
FROM
  PRODUCTOS
WHERE
  PRODUCTOS.precio_venta = (
    SELECT
      MAX(PRODUCTOS.precio_venta)
    from
      PRODUCTOS
  );

/*Obtener el producto mas barato con subconsultas*/
SELECT
  PRODUCTOS.nombre,
  PRODUCTOS.precio_venta as Producto
FROM
  PRODUCTOS
WHERE
  PRODUCTOS.precio_venta = (
    SELECT
      MIN(PRODUCTOS.precio_venta)
    from
      PRODUCTOS
  );

/*Selecciona el promedio de los productos*/
SELECT
  AVG(PRODUCTOS.precio_venta) as Promedio
FROM
  PRODUCTOS;

/*Selecciona todas las ordenes de venta que terminaron siendo nulas*/
select
  orden_venta.reg
from
  orden_venta
  left join (
    select
      *
    from
      orden_venta
      inner join detalle_orden_venta on detalle_orden_venta.orden_venta = ORDEN_VENTA.reg
  ) as OVD on orden_venta.reg = OVD.orden_venta
where
  OVD.orden_venta is null;

/*Selecciona todos los productos que no se han vendido*/
SELECT
  *
FROM
  PRODUCTOS
  LEFT JOIN DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.producto = PRODUCTOS.codigo
where
  orden_venta is null;

/*Seleccionar todos los productos que no se han vendido con subconsultas*/
SELECT
  PRODUCTOS.nombre
fROM
  PRODUCTOS
  LEFT JOIN (
    SELECT
      *
    FROM
      PRODUCTOS
      INNER JOIN DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.producto = PRODUCTOS.codigo
      inner join orden_venta on orden_venta.reg = DETALLE_ORDEN_VENTA.orden_venta
  ) as PV on PV.producto = productos.codigo
where
  PV.producto is null;

/*Mostrar el cliente que ha hecho la compra mas cara*/
SELECT
  CTA.cliente
from
  (
    SELECT
      DOP.cliente,
      SUM(total) as total_acumulado
    from
      (
        SELECT
          CLIENTES.n_cliente,
          CLIENTES.nombre as cliente,
          (
            PRODUCTOS.precio_venta * DETALLE_ORDEN_VENTA.cantidad * 16
          ) + PRODUCTOS.precio_venta * DETALLE_ORDEN_VENTA.cantidad as total
        from
          CLIENTES
          join ORDEN_VENTA on ORDEN_VENTA.cliente = CLIENTES.n_cliente
          join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.orden_venta = orden_venta.reg
          join PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_VENTA.producto
      ) as DOP
    group by
      DOP.n_cliente
  ) as CTA
group by
  CTA.total_acumulado desc;

/*Mostrar productos con su categoria*/
SELECT
  *
FROM
  PRODUCTOS
  LEFT JOIN CATEGORIA_PRODUCTOS on PRODUCTOS.categoria = CATEGORIA_PRODUCTOS.id;

/*Mostrar la cantidad de Productos que tengan las categorias*/
SELECT
  PRODUCTOS.categoria,
  CATEGORIA_PRODUCTOS.categoria,
  COUNT(PRODUCTOS.categoria) as Productos
from
  PRODUCTOS
  join CATEGORIA_PRODUCTOS on CATEGORIA_PRODUCTOS.id = PRODUCTOS.categoria
GROUP BY
  PRODUCTOS.nombre;

/*Mostrar la cantidad de productos que tengan las categorias con subconsultas*/
SELECT
  PCC.Categoria,
  count(PCC.Categoria) as Productos
from
  (
    Select
      PRODUCTOS.nombre as Producto,
      CATEGORIA_PRODUCTOS.categoria as Categoria
    from
      PRODUCTOS
      join CATEGORIA_PRODUCTOS on CATEGORIA_PRODUCTOS.id = PRODUCTOS.categoria
  ) as PCC
group by
  PCC.Categoria;

/*MOSTRAR PRODUCTOS CON SOLO UNA CATEGORIA*/
SELECT
  CPPC.Categoria
from
  (
    SELECT
      PCC.Categoria,
      count(PCC.Categoria) as Productos
    from
      (
        Select
          PRODUCTOS.nombre as Producto,
          CATEGORIA_PRODUCTOS.categoria as Categoria
        from
          PRODUCTOS
          join CATEGORIA_PRODUCTOS on CATEGORIA_PRODUCTOS.id = PRODUCTOS.categoria
      ) as PCC
    group by
      PCC.Categoria
  ) as CPPC
WHERE
  CPPC.Productos = 1;

/*MOSTRAR PRODUCTOS CON MAS DE UNA CATEGORIA*/
SELECT
  CPPC.Categoria
from
  (
    SELECT
      PCC.Categoria,
      count(PCC.Categoria) as Productos
    from
      (
        Select
          PRODUCTOS.nombre as Producto,
          CATEGORIA_PRODUCTOS.categoria as Categoria
        from
          PRODUCTOS
          join CATEGORIA_PRODUCTOS on CATEGORIA_PRODUCTOS.id = PRODUCTOS.categoria
      ) as PCC
    group by
      PCC.Categoria
  ) as CPPC
WHERE
  CPPC.Productos > 1;

/*PRODUCTOS NO VENDIDOS EN DETERMINADO PERIODO*/
SELECT
  PDV.Producto,
  PDV.Fecha
from
  (
    SELECT
      PRODUCTOS.nombre as Producto,
      ORDEN_VENTA.fecha as Fecha
    FROM
      PRODUCTOS
      left join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.producto = PRODUCTOS.codigo
      left join ORDEN_VENTA on ORDEN_VENTA.reg = DETALLE_ORDEN_VENTA.orden_venta
  ) as PDV
where
  PDV.Fecha is null;

/*Productos no vendidos en determinado periodo con al menos 100 existencias*/
SELECT
  PDV.Producto
from
  (
    SELECT
      PRODUCTOS.nombre as Producto,
      ORDEN_VENTA.fecha as Fecha,
      PRODUCTOS.existencias as Existencias
    FROM
      PRODUCTOS
      left join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.producto = PRODUCTOS.codigo
      left join ORDEN_VENTA on ORDEN_VENTA.reg = DETALLE_ORDEN_VENTA.orden_venta
  ) as PDV
where
  PDV.Fecha is null
  and PDV.Existencias > 100;

/* Tarea: */
/* Mostrar el detalle de los productos comprados en una determinada orden venta
 orden_venta/fecha/clave.producto/Producto/Subtotal/iva/total*/
SELECT
  *
from
  (
    select
      ORDEN_VENTA.reg as orden_venta,
      ORDEN_VENTA.fecha,
      PRODUCTOS.codigo as codigo_producto,
      PRODUCTOS.nombre,
      PRODUCTOS.precio_venta * DETALLE_ORDEN_VENTA.cantidad as Subtotal,
      PRODUCTOS.precio_venta * DETALLE_ORDEN_VENTA.cantidad *.16 as IVA,
      (
        PRODUCTOS.precio_venta * DETALLE_ORDEN_VENTA.cantidad *.16
      ) + (
        PRODUCTOS.precio_venta * DETALLE_ORDEN_VENTA.cantidad
      ) as Total
    from
      PRODUCTOS
      JOIN DETALLE_ORDEN_VENTA ON DETALLE_ORDEN_VENTA.producto = PRODUCTOS.codigo
      join ORDEN_VENTA on ORDEN_VENTA.reg = DETALLE_ORDEN_VENTA.orden_venta
  ) as DOP
where
  DOP.orden_venta = '12';

/*Mostrar los productos que no comprados en determinado orden.venta*/
SELECT
  DPV.Producto
from
  (
    Select
      PRODUCTOS.codigo as codigo_producto,
      PRODUCTOS.nombre as Producto,
      ORDEN_VENTA.reg as orden_venta
    from
      PRODUCTOS
      left join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.producto = PRODUCTOS.codigo
      left join ORDEN_VENTA on ORDEN_VENTA.reg = DETALLE_ORDEN_VENTA.orden_venta
  ) as DPV
where
  not DPV.orden_venta = 15;

/*Mostrar clientes que no han comprado*/
SELECT
  CO.cliente
from
  (
    select
      CLIENTES.nombre as cliente,
      ORDEN_VENTA.cliente as codigo_venta_cliente
    from
      CLIENTES
      left join ORDEN_VENTA on ORDEN_VENTA.reg = CLIENTES.n_cliente
  ) as CO
where
  CO.codigo_venta_cliente is null;

/*Mostrar clientes que no compraron en determinado periodo*/
SELECT
  CO.cliente
from
  (
    select
      CLIENTES.nombre as cliente,
      ORDEN_VENTA.cliente as codigo_venta_cliente,
      ORDEN_VENTA.fecha
    from
      CLIENTES
      left join ORDEN_VENTA on ORDEN_VENTA.reg = CLIENTES.n_cliente
  ) as CO
where
  CO.fecha is null;

/*Detalle de compra acumulada por cliente*/
SELECT
  DOV.cliente,
  SUM(DOV.total) as total_acumulado
from
  (
    SELECT
      CLIENTES.n_cliente,
      CLIENTES.nombre as cliente,
      orden_venta.reg as orden_venta,
      (
        detalle_orden_venta.cantidad * PRODUCTOS.precio_venta *.16
      ) + detalle_orden_venta.cantidad * PRODUCTOS.precio_venta as total
    from
      CLIENTES
      join ORDEN_VENTA on ORDEN_VENTA.cliente = CLIENTES.n_cliente
      join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.orden_venta = orden_venta.reg
      join PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_VENTA.producto
  ) as DOV
group by
  DOV.n_cliente;

/*Mostrar promedio de ventas*/
SELECT
  AVG(DVP.total) as PROMEDIO
from
  (
    SELECT
      orden_venta.reg,
      (
        DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta *.16
      ) + (
        DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta
      ) as TOTAL
    from
      ORDEN_VENTA
      join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.orden_venta = ORDEN_VENTA.reg
      join PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_VENTA.producto
  ) as DVP;

/*Mostrar promedio de ventas en determinado periodo*/
SELECT
  AVG(DVP.total)
from
  (
    SELECT
      orden_venta.reg,
      orden_venta.fecha,
      (
        DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta *.16
      ) + (
        DETALLE_ORDEN_VENTA.cantidad * PRODUCTOS.precio_venta
      ) as TOTAL
    from
      ORDEN_VENTA
      join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.orden_venta = ORDEN_VENTA.reg
      join PRODUCTOS on PRODUCTOS.codigo = DETALLE_ORDEN_VENTA.producto
  ) as DVP
where
  DVP.fecha = '2022-05-16 10:43:18';

/*Mostrar los productos no vendidos en el ultimo mes y aplicarles un 20% de descuento*/
SELECT
  PDV.Producto,
  PDV.precio_con_iva,
  PDV.precio_con_iva *.20 as Descuento,
  PDV.precio_con_iva *.80 as precio_con_descuento
from
  (
    SELECT
      PRODUCTOS.nombre as Producto,
      ORDEN_VENTA.fecha as Fecha,
      (PRODUCTOS.precio_venta *.16) + (PRODUCTOS.precio_venta) as precio_con_iva
    FROM
      PRODUCTOS
      left join DETALLE_ORDEN_VENTA on DETALLE_ORDEN_VENTA.producto = PRODUCTOS.codigo
      left join ORDEN_VENTA on ORDEN_VENTA.reg = DETALLE_ORDEN_VENTA.orden_venta
  ) as PDV
where
  PDV.Fecha is null;