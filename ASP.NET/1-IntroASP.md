# Intro ASP 
* Comando para conectarme a la base de datos : 
**Scaffold-DbContext "Server=.;Database=Pub;Trusted_Connection=true;" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models**

Server = Nombre del server

Database = Nombre de la base de datos

-Si añadimos -force al comando anterior se actualiza la base de datos si tenemos cambios en la clase.