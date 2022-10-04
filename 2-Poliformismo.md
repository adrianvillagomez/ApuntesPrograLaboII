# Polimorfismo

* Ejemplo visto en clase
```c#
namespace Consola
{
    internal class Program
    {
        static void Main(string [] args)
        {
            Animal animal = new Animal("Pepe Peposo",12);
            Animal animal1 = new Gato("Salem", 500);
            Gato gato = new Gato("Bola de Nieve", 5 );

            Console.WriteLine($"Tipo: {animal.GetType().Name} {animal.EmitirSonido()}");
            Console.WriteLine($"Tipo: {animal1.GetType().Name} {animal1.EmitirSonido()}");
            Console.WriteLine(animal1.Equals(null));
           
        }
    }
}
namespace Biblioteca
{
    public class Animal
    {
        protected int id;
        string nombre;
        int edad;

        public Animal(string nombre, int edad)
        {
            this.nombre = nombre;
            this.edad = edad;
        }

        public virtual string EmitirSonido()
        {
            return "como";
        }
        public static bool operator ==(Animal a1, Animal a2)
        {
            return a1 is not null &&
                a2 is not null &&
                a1.nombre == a2.nombre &&
                a1.edad == a2.edad;
        }
        public static bool operator !=(Animal a1, Animal a2)
        {
            return !(a1 == a2);
        }
        public override bool Equals(object obj)
        {
            return this == (Animal) obj;
        }

    }
}
namespace Biblioteca
{
    public  class Gato : Animal
    {
        bool tienePulgas;
       
        public Gato(string nombre, int edad):base(nombre, edad)
        {
            tienePulgas = false;
        }
        public override string EmitirSonido()
        {
            return base.EmitirSonido()+ " gato: Meeww";
        }
     
        public static bool operator ==(Gato g1, Gato g2)
        {
            return (Animal)g1 == g2 && g1.tienePulgas == g2.tienePulgas;
        }
        public static bool operator !=(Gato g1, Gato g2)
        {
            return !(g1 == g2);
        }
        public override bool Equals(object obj)
        {
            Gato gato = obj as Gato;
            return gato is not null && this == (Gato)obj;
        }
        public override int GetHashCode()
        {
            return this.id.GetHashCode();
        }
    }
}
```
## Clase abstracta

 * Ejemplo de clase abstracta con propiedades y metodos abstractos.

```c#
public abstract class Sobreescrito
    {
        public int i = 0;
        protected string miAtributo;
        public Sobreescrito()
        {
            this.miAtributo = "Probar Abstractos";
        }

        public override string ToString()
        {
            return $"¡Este es mi método ToString sobrescrito!";
        }
        public override bool Equals(object obj)
        {
            //return this==obj;
            return obj is Sobreescrito;
        }
        public override int GetHashCode()
        {
            return i = 1142510181;
        }
        protected abstract string MiPropiedad
        {
            get;
        }
        public abstract string MiMetodo();
        
    }
//Clase hija
 public class SobreSobreescrito : Sobreescrito
    {
        public SobreSobreescrito():base()
        {          
        }
        public override string MiMetodo()
        {
            return base.miAtributo;
        }
        protected override string MiPropiedad
        {
            get
            {
                return MiMetodo();
            }
        }
        
    }

```