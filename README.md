# money-sim (Java + Tomcat)

Simulación simple de transferencias entre dos usuarios (emisor y receptor) usando Servlets/JSP en Tomcat. Los saldos se mantienen en memoria (no persistente).

## Requisitos
- JDK 11+
- Maven 3.6+
- Tomcat 9+ (o compatible con Servlet 4.0)

## Estructura del proyecto
```
money-sim/
├─ pom.xml
├─ src/
│  └─ main/
│     ├─ java/
│     │  └─ com/example/moneysim/
│     │     ├─ AccountStore.java
│     │     ├─ AppInitializer.java
│     │     ├─ BalanceServlet.java
│     │     └─ TransferServlet.java
│     └─ webapp/
│        ├─ sender.jsp
│        ├─ receiver.jsp
│        └─ WEB-INF/
│           └─ web.xml
```

## Compilar y empaquetar
Desde la raíz del proyecto (`money-sim/`):

```bash
mvn clean package
```

Se generará `target/money-sim.war`.

## Despliegue en Tomcat
1. Copia `target/money-sim.war` a `TOMCAT_HOME/webapps/`.
2. Inicia Tomcat.
3. Accede desde el navegador:
   - Emisor (formulario de transferencia): `http://<IP_DEL_SERVIDOR>:8080/money-sim/sender.jsp`
   - Receptor (consulta de saldo): `http://<IP_DEL_SERVIDOR>:8080/money-sim/receiver.jsp`

> Reemplaza `<IP_DEL_SERVIDOR>` por la IP o `localhost` si navegas en el mismo equipo.

## Notas
- Los saldos se pierden al reiniciar (almacenamiento en memoria).
- No incluye autenticación ni seguridad; solo para fines educativos.
- Si quieres agregar confirmación del receptor o persistencia, extiende la lógica en `AccountStore` y añade nuevos servlets/JSPs.
