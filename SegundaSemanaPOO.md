# POO

* Atributos de clase siempre en private,se acceden y se modifican mediante Setter y Getters a esto llamamos encapsulamiento

* Si el atributo es STATIC significa que es atributo de clase y no nesecita una estancia de clase osea un constructor en el main

* Para los Getter y Setter de los atributos STATIC el metodo tambien es Static

```c#
namespace Entidades
{
    public class Auto// si la clase es static Sus métodos no se asocian a un objeto particular sino a la clase
    {       
        //Clase de instancia
        /*
         * Si el metodo es es Static se accede mediante Auto.
         * Si es public string se accede mediante el objeto creado (ejem "a1")
        */
        // ATRIBUTOS DE LA CLASE--Mienbros de Instancias
        private string patente;
        private string marca;
        private string modelo;
        private int cantidadHora;
        private static float precioHora; // atributo estatico
        //STATIC Es un modificador que permite ejecutar un método sin tener que instanciar una variable (sin crear un objeto)
        static Auto()
        {
            Auto.precioHora = 100f;
        }
        //CONSTRUCTOR
        public Auto (string patente,string marca,string modelo)
        {
            this.patente = patente;
            this.marca = marca;
            this.modelo = modelo;
        }
        
        //Getters y Setters ---- Encapsulamiento
        //Se accede mediante AUTO.-- METODO STATICO
        public static float GetPrecioHora()
        {
            return Auto.precioHora;
        }
        public static void SetPrecioHora(float value)//NO Puedo usar el operador “this” dentro de un método estático
        {
            Auto.precioHora = value;
        }
        //Getters y Setters ---- Encapsulamiento
        public string GetPatente ()
        {
            return this.patente;
        }
        public void SetPatente (string value)
        {
            if (string.IsNullOrEmpty (value))
            {
                this.patente = value;
            }
        }
        public string GetMarca()
        {
            return this.marca;
        }
        public void SetMarca(string value)
        {
            if (string.IsNullOrEmpty(value))
            {
                this.marca = value;
            }
        }
        public string GetModelo()
        {
            return this.modelo;
        }
        public void SetModelo(string value)
        {
            if (string.IsNullOrEmpty(value))
            {
                this.modelo = value;
            }
        }
        public int GetCantidadHora()
        {
            return this.cantidadHora;
        }
        public void SetCantidadHora(int value)
        {
            if (value > 0)
            { 
                this.cantidadHora = value;
            }
        }

        public float CalcularCostoEstadia()
        {
            return this.cantidadHora * Auto.precioHora;
        }
    }
}

```