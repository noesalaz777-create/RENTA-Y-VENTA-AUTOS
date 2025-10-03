# RENTA-Y-VENTA-AUTOS
Creación de un sistema para el Registro de Renta  y venta de autos, donde se debe de Llevar control de venta y renta carros, sucursales, anticipo, depreciación, roles de usuario, factura, 

CREATE TABLE Administrador (
	ID_Administrador int not null identity primary key,
	genero char(1) not null,
	DocumentoIdentificacion varchar(100),
	nombreCompleto varchar(100) not null,
	Fecha_Nacimiento date not null,
	Direccion varchar(100)not null,
	Telefono varchar(9) not null,
);

CREATE TABLE Vendedor (
	ID_vendedor int not null identity primary key,
	genero char(1) not null,
	DocumentoIdentificacion varchar(100),
	nombreCompleto varchar(100) not null,
	Fecha_Nacimiento date not null,
	Direccion varchar(100)not null,
	Telefono varchar(9) not null,
);

CREATE TABLE Cliente (
	ID_Cliente int not null identity primary key,
	genero char(1) not null,
	DocumentoIdentificacion varchar(100),
	nombreCompleto varchar(100) not null,
	Fecha_Nacimiento date not null,
	Direccion varchar(100)not null,
	Telefono varchar(9) not null,
);

CREATE TABLE Usuarios (
    usuario_id INT PRIMARY KEY,
    nombre_usuario VARCHAR(50) NOT NULL ,
    contrasena_hash VARCHAR(100) NOT NULL, 
    email VARCHAR(100) ,
    fecha_creacion DATE
);

CREATE TABLE Usuario_Roles (
    usuario_id INT,
    rol_id INT,
    PRIMARY KEY (usuario_id, rol_id),
    FOREIGN KEY (usuario_id) REFERENCES Usuarios(usuario_id),
    FOREIGN KEY (rol_id) REFERENCES Roles(rol_id)
	);

CREATE TABLE carros (
id_carro INT PRIMARY KEY IDENTITY(1,1)NOT NULL,
marca VARCHAR (50)NOT NULL,
modelo VARCHAR (50)NOT NULL,
año DATETIME NOT NULL,
precio DECIMAL (1,1)NOT NULL,
disponible VARCHAR (50)NOT NULL,
fecha_ingreso DATETIME NOT NULL,
color VARCHAR (30)NOT NULL,

);
CREATE TABLE VentasAutos (
    id_venta INT  PRIMARY KEY,
    id_cliente INT,
    id_auto INT UNIQUE,
    id_vendedor INT,
    fecha_venta DATE NOT NULL,
    precio_final DECIMAL(10,2),
    metodo_pago VARCHAR(30),
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente),
    FOREIGN KEY (id_auto) REFERENCES Autos(id_auto),
    FOREIGN KEY (id_vendedor) REFERENCES Vendedores(id_vendedor)
);
CREATE TABLE VentasAutos (
    id_venta INT  PRIMARY KEY,
    id_cliente INT,
    id_auto INT UNIQUE,
    id_vendedor INT,
    fecha_venta DATE NOT NULL,
    precio_final DECIMAL(10,2),
    metodo_pago VARCHAR(30),
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente),
    FOREIGN KEY (id_auto) REFERENCES Autos(id_auto),
    FOREIGN KEY (id_vendedor) REFERENCES Vendedores(id_vendedor)
);
