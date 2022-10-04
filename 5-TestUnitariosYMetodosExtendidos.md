# Test unitarios Y metodos extendido

* Ejemplo de metodo INT extendido con fizzbuzz
```c#
namespace Entidades
{
    public static class Int32Extendido
    {
        public static string  FizzBuzz(this int e)
        {
            string resultado = string.Empty;
            if(e % 3 == 0)
            {
                resultado += "Fizz";
            } 
            if (e % 5 == 0)
            {
                resultado += "Buzz";
            }
            if(string.IsNullOrEmpty(resultado))
            {
                resultado += e.ToString();
            }
            return resultado;
        }
    }
}
```
* Ejecutado en el program 
```c#
 public class Program
    {
        static void Main(string[] args)
        {
            for(int i = 0; i < 20; i++)
            {
                Console.WriteLine(i.FizzBuzz());
            }
        }
    }
```

* Test al metodo FizzBuzz
```c#
namespace TestProject1
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void FizzBuzz_ElNumeroEsDivisibleSoloPor3_DeberiaDevolverFizz()
        {
            //Arrange
            int numero = 3;
            string expected = "Fizz";
            //Act
            string actual = numero.FizzBuzz();
            //Assert
            Assert.AreEqual(expected, actual);
        }
        [TestMethod]
        public void FizzBuzz_ElNumeroEsDivisibleSoloPor5_DeberiaDevolverBuzz()
        {
            //Arrange
            int n = 5;
            string expected = "Buzz";
            //Act
            string actual = n.FizzBuzz();
            //Assert
            Assert.AreEqual(expected , actual);

        }
        [TestMethod]
        public void FizzBuzz_ElNumeroEsDivisibleSoloPor5y3_DeberiaDevolverFizzBuzz()
        {
            //Arrange
            int n = 15;
            string expected = "FizzBuzz";
            //Act
            string actual = n.FizzBuzz();
            //Assert
            Assert.AreEqual (expected , actual);

        }
        [TestMethod]
        [DataRow(2,"2")]
        [DataRow(4, "4")]
        [DataRow(1, "1")]
        public void FizzBuzz_ElNumeroNoEsDivisiblePor5y3_DeberiaRetornarElNumero(int n,string expected)
        {
            //Actual
            string actual = n.FizzBuzz();
            //Assert
            Assert.AreEqual(expected,actual);
        }
    }
}
```