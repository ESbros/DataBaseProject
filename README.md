# DataBaseProject
A PostgreSQL database project oriented for a "Trekking Club". Interface developed on Visual Basic.

FinalProjectV1.0(VisualBasicCode).zip is a file containing the code developed on Visual Basic.

FPExecutable.zip contains the executable for the program. (Runs only on Windows)

PostgreSQL queries for creating the corresponding tables:

          create table miembro (id_miembro bigint, nombre varchar, apellido varchar, fecha_nac date, fecha_ingreso date, mail, varchar, telefono bigint);
          alter table miembro add constraint pkIDmiembro primary key (id_miembro);

          create table cargos (id_cargo serial, descripcion varchar);
          alter table cargos add constraint pkIDcargo primary key (id_cargo);

          create table directiva (id_cargo serial, descripcion varchar, id_miembro int, fecha_inicio date);
          alter table directiva add constraint pkDirectiva primary key (id_miembro);

          create table destino (id_destino serial, ubicacion varchar, nivel varchar);
          alter table destino add constraint pkIDdestino primary key (id_destino, ubicacion);

          create table transporte (id_transporte serial, placa varchar, tipo varchar, nro_ascientos int);
          alter table transporte add constraint pkTransporte primary key (placa);

          create table viaje (id_viaje serial, fecha date, id_destino int, id_transporte int, cuota money);
          alter table viaje add constraint pkIDviaje primary key (id_viaje);

          create table reunion (id_reunion serial, tema varchar, ubicacion varchar, fecha date);
          alter table reunion add constraint pkIDreunion primary key (id_reunion);

          create table asistio_d (id_miembro bigint, id_viaje int, cuota money);
          alter table asistio_d add constraint pkIDasistioV primary key (id_miembro, id_viaje);
          alter table asistio_d add constraint fkVmiembro foreign key(id_miembro) references miembro(id_miembro);
          alter table asistio_d add constraint fkVviaje foreign key(id_viaje) references viaje(id_viaje);

          create table asistio_r (id_miembro bigint, id_reunion int);
          alter table asistio_r add constraint pkIDasistioD primary key (id_miembro, id_reunion);
          alter table asistio_r add constraint fkRmiembro foreign key(id_miembro) references miembro(id_miembro);
          alter table asistio_r add constraint fkRviaje foreign key(id_reunion) references reunion(id_reunion);

          alter table miembro add constraint cIDmiem check(id_miembro > 999999999);
          alter table miembro add constraint cTelmiem check(telefono > 99999999);

