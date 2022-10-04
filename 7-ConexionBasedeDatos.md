# Conexion a bases de datos

## Leer datos de base de Datos READ
* Leer datos de una base de datos SQL
* Instalar paquete nuGets System.Data.SqlClient
* agregar using System.Data.SqlClient;
* ExecuteReader para leer
```c#
 public class GestorSQL
    {
        private static string cadenaConexion;
        static GestorSQL()
        {
            GestorSQL.cadenaConexion = "Server=.;Database=DIV2EClase17;Trusted_Connection=True;";
            //esta ruta se usa siempre solo modifico el campo Database
        }


        public static List<Persona> LeerDatos()
        {
            List<Persona> personas = new List<Persona>();

            string query = "select * from personas";
            using (SqlConnection connection = new SqlConnection(GestorSQL.cadenaConexion))
            {
                SqlCommand cmd = new SqlCommand(query, connection);
                connection.Open();//abrir la conexion
                SqlDataReader reader = cmd.ExecuteReader();
                //Mientras pueda leer - tenga contenido en mi reader--lee fila a fila
                while (reader.Read())
                {
                    int id = reader.GetInt32(0);//0 es donde incia la fila
                    string nombre = reader.GetString(1);//reader["nombre"].ToString(); otra forma
                    string apellido = reader.GetString(2);
                    string email = reader.GetString(3);
                    string sexo = reader.GetString(4);
                    int edad = reader.GetInt32(5);
                    Persona persona = new Persona(id, nombre, email, apellido, sexo, edad);
                    personas.Add(persona);
                }    
            }
            return personas;
        }
    }
    //En el main
      static void Main(string[] args)
        {
            try
            {
                List<Persona> personas = GestorSQL.LeerDatos();

                foreach (Persona item in personas)
                {
                    Console.WriteLine(item.ToString());
                    Console.ReadKey();
                }
            }catch(Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }

```
* Leer un dato especifico en este caso por id
* aplicando seguridad anti inyeccion sql
* se agrea el parameters.addwithvalue de la instancia de sqlcommand
```c#
  public static Persona LeerDatosPorId(int id)
        {
            Persona persona= null;

            string query = "select * from personas where id=@id";
            using (SqlConnection connection = new SqlConnection(GestorSQL.cadenaConexion))
            {
                SqlCommand cmd = new SqlCommand(query, connection);
                cmd.Parameters.AddWithValue("id",id);
                connection.Open();
                SqlDataReader reader = cmd.ExecuteReader();

                while (reader.Read())
                {
  
                    string nombre = reader.GetString(1);
                    string apellido = reader.GetString(2);
                    string email = reader.GetString(3);
                    string sexo = reader.GetString(4);
                    int edad = reader.GetInt32(5);
                    persona = new Persona(id, nombre, email, apellido, sexo, edad);

                }
            }

            return persona;
        }
        //Main
         static void Main(string[] args)
        {
            try
            {
                Persona p = GestorSQL.LeerDatosPorId(1001);
                Console.WriteLine(p.ToString());
            }catch(Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
```
# Alta
* insertar un objeto persona a mi base de datos
* Guardar datos en una base de datos
```c#
  public static void Alta(Persona persona)
        {
            string query = "insert into personas (nombre, apellido, email, sexo, edad) values (@nombre,@apellido,@email,@sexo,@edad)";
            SqlConnection connection = null;
            try
            {
                connection = new SqlConnection(GestorSQL.cadenaConexion);
                connection.Open();
                SqlCommand cmd = new SqlCommand(query,connection);
                cmd.Parameters.AddWithValue("nombre", persona.Nombre);
                cmd.Parameters.AddWithValue("apellido", persona.Apellido);
                cmd.Parameters.AddWithValue("email", persona.Email);
                cmd.Parameters.AddWithValue("sexo", persona.Sexo);
                cmd.Parameters.AddWithValue("edad", persona.Edad);
                cmd.ExecuteNonQuery();
            }
            catch (Exception)
            {
                throw;
            }
            finally
            {
                if(connection != null && connection.State == System.Data.ConnectionState.Open)
                {
                    connection.Close(); 
                }
            }
        }
        //Main
        static void Main(string[] args)
        {
            try
            {
                
                Persona nuevaP = new Persona("Franco", "email@mail.com.ar", "Messina", "Male", 40);
                GestorSQL.Alta(nuevaP);
            }catch(Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
```
# Baja
* En este caso borramos por ID
```c#
 public static void Borrar(int id)
        {


            string query = "delete from personas where id = @id";
            using (SqlConnection connection = new SqlConnection(GestorSQL.cadenaConexion))
            {
                SqlCommand cmd = new SqlCommand(query, connection);
                cmd.Parameters.AddWithValue("id", id);
                connection.Open();
                cmd.ExecuteNonQuery();
            }
        }
        //MAIN
         static void Main(string[] args)
        {
            try
            {
                  GestorSQL.Borrar(1);
                Console.WriteLine("Ya borre");               
            }catch(Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
```
# Modificar/actualizar
* Modificar datos de mi base de datos "persona"
```c#
 public static void Actualizar(Persona persona, int id)
        {


            string query = "update personas set nombre=@nombre, apellido=@apellido, email=@email, sexo=@sexo, edad=@edad where id = @id";
            using (SqlConnection connection = new SqlConnection(GestorSQL.cadenaConexion))
            {
                SqlCommand cmd = new SqlCommand(query, connection);
                cmd.Parameters.AddWithValue("id", id);
                cmd.Parameters.AddWithValue("nombre", persona.Nombre);
                cmd.Parameters.AddWithValue("apellido", persona.Apellido);
                cmd.Parameters.AddWithValue("email", persona.Email);
                cmd.Parameters.AddWithValue("sexo", persona.Sexo);
                cmd.Parameters.AddWithValue("edad", persona.Edad);
                connection.Open();
                cmd.ExecuteNonQuery();
            }
        }
        //Main
  static void Main(string[] args)
        {
            try
            {
                Persona p = new Persona("Franco", "email@mail.com.ar", "Messina", "Male", 40);
                GestorSQL.Actualizar(p, 2);
                Console.WriteLine("Ya Actualice");            
            }catch(Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }       
```