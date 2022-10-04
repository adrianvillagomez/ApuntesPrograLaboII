# Ejemplo Como usar Linq con clases
* Clase control Empresas donde se ejecuta las instrucciones LINQ
```c#
 public class ControlEmpresasEmpleados
    {
        public List<Empresa> listaEmpresas;
        public List<Empleado> listaEmpleados;

        public ControlEmpresasEmpleados()
        {
            this.listaEmpresas = new List<Empresa>();
            this.listaEmpleados =new List<Empleado>();
            listaEmpresas.Add(new Empresa { Id = 1, Nombre = "Google" });
            listaEmpresas.Add(new Empresa { Id = 2, Nombre = "Pildoras" });
            listaEmpleados.Add(new Empleado { Id = 1, Nombre = "Juan", Cargo = "CEO", EmpresaId = 1, Salario = 1500 });
            listaEmpleados.Add(new Empleado { Id = 2, Nombre = "Diaz", Cargo = "CEO", EmpresaId = 2, Salario = 1400 });
            listaEmpleados.Add(new Empleado { Id = 3, Nombre = "Larry", Cargo = "CO-CEO", EmpresaId = 1, Salario = 1800 });
            listaEmpleados.Add(new Empleado { Id = 4, Nombre = "Maria", Cargo = "Administrativo", EmpresaId = 2, Salario = 1900 });
        }
        /// <summary>
        /// Devulve empleados que sean Ceos con linq
        /// </summary>
        public void GetCeo()
        {
            IEnumerable<Empleado> ceos = from empleado in listaEmpleados where empleado.Cargo == "CEO" select empleado;
            foreach (Empleado item in ceos)
            {
                item.getDatosEmpleado();
            }
        }
        public void GetCantidad()
        {
            IEnumerable<Empleado> ceos = from empleado in listaEmpleados where empleado.Cargo == "CEO" select empleado;
            int cantidad = ceos.Count();
            Console.WriteLine(cantidad);
        }
        /// <summary>
        /// Ordena mis empleados utilizando la consulta orderby y si agregamos descending lo ordena al revez
        /// </summary>
        public void GetEmpleadosOrdenados()
        {
            IEnumerable<Empleado> empleados = from empleado in listaEmpleados orderby empleado.Nombre descending select empleado;
            foreach (Empleado item in empleados)
            {
                item.getDatosEmpleado();
            }
        }
        /// <summary>
        /// devuelve los empleados que pérteneces a la empres pildoras
        /// </summary>
        public void GetEmpleadosPildoras()
        {
            IEnumerable<Empleado> empleadosPildoras = from empleado in listaEmpleados
                                              join empresa in listaEmpresas
                                              on empleado.EmpresaId equals empresa.Id
                                              where empresa.Nombre == "Pildoras"
                                              select empleado;
            foreach (Empleado item in empleadosPildoras)
            {
                item.getDatosEmpleado(); 
            }
        }
         /// <summary>
        /// Devuelve los empleados a los que pertecenen a la empresas por el id del parametro
        /// </summary>
        /// <param name="id"></param>
        public void GetEmpledaosEmpresa(int id)
        {

            IEnumerable<Empleado> empleadosEmpresas = from empleado in listaEmpleados
                                                      join empresa in listaEmpresas
                                                      on empleado.EmpresaId equals empresa.Id
                                                      where empresa.Id == id
                                                      select empleado;
            foreach (Empleado item in empleadosEmpresas)
            {
                item.getDatosEmpleado();
            }
        }
    }
```
* Main
```c#
  static void Main(string[] args)
        {
            // Linq con ejemplo simple 
            int[] valoresNumnericos = new int[] {1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
            Console.WriteLine("Numeros Pares");
          
            IEnumerable<int>numerosPares = from numero in valoresNumnericos where numero % 2 == 0 select numero;
            foreach (int item in numerosPares)
            {
                Console.WriteLine(item);
            }
            //Linq con ejemplo de clases
            ControlEmpresasEmpleados main = new ControlEmpresasEmpleados();
            main.GetCeo();
            Console.WriteLine("-----------------------");
            main.GetCantidad();
            Console.WriteLine("-----------------------");
            main.GetEmpleadosOrdenados();
            Console.WriteLine("-----------------------");
            main.GetEmpleadosPildoras();
            Console.WriteLine("-----------------------");
            main.GetEmpledaosEmpresa(1);
        }
```
* clase Empresa y Empleado
```c#
 public class Empleado
    {
        public int Id { get; set; }
        public string Nombre { get; set; }
        public string Cargo { get; set; }  
        public double Salario { get; set; }
        //Clave foranea
        public int EmpresaId { get; set; }
        public void getDatosEmpleado()
        {
            Console.WriteLine("Empleado {0} con id {1},Cargo {2} con salario {3} y " +
                "pertenece a la Empresa {4}", Nombre, Id,Cargo,Salario,EmpresaId);
        }
    }
    public class Empresa 
    {
        public int Id { get; set; }
        public string Nombre { get; set; }
       public void getDatosEMpresa()
        {
            Console.WriteLine("Empresa {0} con id {1}", Nombre, Id);
        }
    }

```