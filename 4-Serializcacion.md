# Serializacion XLM
* 2 metodos de serializar
* Siempre un constructor publico sin parametros
```c#
 public class Serializadora
    {
        private static string rutaBase;

        static Serializadora()
        {
            DirectoryInfo path = Directory.CreateDirectory($"{Environment.GetFolderPath(Environment.SpecialFolder.Desktop)}\\Archivos_Serializados\\");
            Serializadora.rutaBase = path.FullName;
        }


        public static void Serializar_StreamWriter(string nombreArchivo,Persona persona)
        {
            using (StreamWriter streamWriter = new StreamWriter($"{Serializadora.rutaBase}{nombreArchivo}"))
            {
                XmlSerializer xml = new XmlSerializer(typeof(Persona));

                xml.Serialize(streamWriter, persona);

            }
        }
        public static void Serializar_XmlTextWriter(string nombreArchivo, Persona persona)
        {

            using (XmlTextWriter xmlTextWriter = new XmlTextWriter($"{Serializadora.rutaBase}{nombreArchivo}", Encoding.UTF8))
            {
                XmlSerializer xml = new XmlSerializer(typeof(Persona));
                xmlTextWriter.Formatting = Formatting.Indented;
                xml.Serialize(xmlTextWriter, persona);

            }
        }
    }
    //Main
    Persona alumno = new Persona("Pepe perez", 34, 7.8f);
    lumno.Materias.Add("Programacion");
    alumno.Materias.Add("laboratorio");
    Serializadora.Serializar_XmlTextWriter("profesorSerializadoHerencia.xml",profesor);
    Console.WriteLine("Ya serialize");
```
* Serealizar en caso de herencia con el xlmInclude le indicamos que al momento de serealizar tiene que incluir la clase q la hereda
```c#
 [XmlInclude(typeof(Alumno)), XmlInclude(typeof(Profesor))]
```
# Deserealizacion XML

```c#
 public static Persona Deserializar_StreamReader(string nombreArchivo)
        {
            using(StreamReader streamReader = new StreamReader($"{Serializadora.rutaBase}{nombreArchivo}"))
            {
                XmlSerializer xml = new XmlSerializer(typeof(Persona));
                Persona persona = xml.Deserialize(streamReader) as Persona;
                return persona;
            }

        }
        public static Persona Deserializar_XmlTextReader(string nombreArchivo)
        {
            using (XmlTextReader xmlTextReader = new XmlTextReader($"{Serializadora.rutaBase}{nombreArchivo}"))
            {
                XmlSerializer xml = new XmlSerializer(typeof(Persona));
                Persona persona = xml.Deserialize(xmlTextReader) as Persona;
                return persona;
            }

        }

// ejemplo de lo que iria en el main solo que reemplazo Persona en mis metodosSerealizar
Persona alumno = Serializadora.Deserializar_XmlTextReader("alumnoSerializado2.xml");
Console.WriteLine("Ya DesSerialize");
Console.WriteLine(alumno.ToString());
```
# Serealizacion JSON

```c#
 public static void Serializar_JSON(string nombreArchivo, Empleado empleado)
        {
            using(StreamWriter streamWriter = new StreamWriter($"{Serializadora.rutaBase}{nombreArchivo}"))
            {            
                JsonSerializerOptions options = new JsonSerializerOptions();
                options.WriteIndented = true;
                string ser = JsonSerializer.Serialize(empleado,options);
                streamWriter.WriteLine(ser);
            }
        }

        //MAIN
Empleado emp = new Empleado();
emp.Nombre = "Jorge";
emp.Apellido = "Lopez";
emp.Tareas.Add("Limpiar");
emp.Tareas.Add("Cocinar");
emp.Tareas.Add("Enseñar");
Serializadora.Serializar_JSON("persona.json", emp);
Console.WriteLine("Ya Serialize");

```
# Deserializacion JSON
```c#
 public static Empleado DesSerializar_JSON(string nombreArchivo)
        {
            using (StreamReader streamReader = new StreamReader($"{Serializadora.rutaBase}{nombreArchivo}"))
            {
                string json = streamReader.ReadToEnd();
                return JsonSerializer.Deserialize<Empleado>(json);
            }
        }
   //Main
Empleado empleadoLeido = Serializadora.DesSerializar_JSON("persona.json");
Console.WriteLine(empleadoLeido.ToString());       
```