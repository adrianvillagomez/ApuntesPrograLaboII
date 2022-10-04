# ARCHIVOS ESCRITURA
* main
```c#
 public class Program
    {
        static void Main(string[] args)
        {
            GestorDeArchivo.Escribir("miArchivoPrueba.txt", "Hola Mundo", true);

            Console.WriteLine("ya escribi");


            //Console.WriteLine($"Contenido del archivo:  {GestorDeArchivo.Leer("miArchivoPrueba.txt")}");

            //Console.WriteLine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop));
            
        }
    }
```
* Primera opcion
```c#
public static class GestorDeArchivo
    {
        static string rutaBase;
        static GestorDeArchivo()
        {
            GestorDeArchivo.rutaBase = Environment.GetFolderPath(Environment.SpecialFolder.Desktop);
        }

        public static bool Escribir(string ruta, string contenido, bool append)
        {
            StreamWriter stremWriter = null;
            try
            {
                string nuevaRuta = $"{GestorDeArchivo.rutaBase}\\{ruta}";
                stremWriter = new StreamWriter(nuevaRuta, append);
                stremWriter.Write(contenido);

            }
            catch (Exception ex)
            {
                throw new ArchivoException("Error al escribir", ex);
            }
            finally
            {
                if (stremWriter != null)
                {
                    stremWriter.Close();
                }
            }


            return true;
        }
    }

```
* segunda opcion de escritura con using ya no es nesecario el bloque finally del try catch
* si la ruta no es especifica la guarda en el proyecto /bin/debug/net5

# Archios Lectura
```c#
 public static string Leer(string ruta)
        {
            string retorno = String.Empty;
            try
            {
                using(StreamReader streamReader =  new StreamReader($"{GestorDeArchivo.rutaBase}\\{ruta}"))
                {
                    for (int i = 0; i < 2; i++)// aca tambien se puede usar read to end
                    {
                        Console.WriteLine(streamReader.ReadLine());
                    }

                    retorno = "";
                }

            }
            catch(Exception ex)
            {
                throw new ArchivoException("Error al leer una archivo", ex);
            }

            return retorno;
        }
```
