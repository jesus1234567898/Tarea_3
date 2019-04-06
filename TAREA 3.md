#Herencia.
---
###Clase base.
Una clase base es aquella que no dependen ninguno de sus atributos u objetos de la clase de alguna otra clase, se podría decir que en términos de herencia, seria la clase padre, la clase que se mantiene fija, en el aspecto de herencia.
Es también por así llamarlo la clase principal de un programa, seria la clase primaria sin incluir la clase `Main` en donde se corre todo el programa en si.

No dependen ninguno de sus atributos u objetos de la clase de alguna otra clase, se podría decir que en términos de herencia, sería la clase padre, la clase que se mantiene fija, en el aspecto de herencia. Es también por así llamarlo la clase principal de un programa, sería la clase primaria sin incluir la clase main en donde se corre todo el programa en sí.


###Clase derivada. 
son clases que dependen de las clases bases, ya que algunos de sus métodos son también heredados, y muchas veces, el compilador arrojara malos resultados, ya que al ser dependientes estas clases, a veces podrán generar errores lógicos.

En la clase derivada se define una función que tiene el mismo nombre y los mismos parámetros que la de la clase base. Se dice que redefinimos la función mostrar en la clase derivada. La función miembro mostrar de la clase derivada `VentanaTitulo` hace una llamada a la función mostrar de la clase base Ventana.



###Herencia simple. 
La herencia es uno de los mecanismos de los lenguajes de programación orientada a objetos basados en clases, por medio del cual una clase se deriva de otra de manera que extiende su funcionalidad. La clase de la que se hereda se suele denominar clase base, clase padre, superclase, clase ancestro (el vocabulario que se utiliza suele depender en gran medida del lenguaje de programación).
La herencia simple es la más típica, la que se puede encontrar en cualquier lenguaje moderno como `Java` o `C#`.

La herencia simple es una relación entre una clase padre (clase base) y una clase hija (clase derivada) llamada "es un tipo de", que muchas veces se abrevia.
La herencia es simple cuando la clase derivada que estamos considerando sólo tiene una clase base.

###Herencia Múltiple.
Cuando heredas atributos de una clase padre a una clase hija, la clase hija no puede recibir más de una herencia, porque se crearía una ambigüedad, por lo que `c#` no acepta las herencias múltiples de las clases hijas.

Pero si lo que se esta hablando es de tomar la herencia de una clase padre a diferentes clases hijas, si es posible que se hereden los atributos de la clase principal. 


###UML Clase figura.
![UML de la clase figura](https://i.ibb.co/bJXdYdp/Clase-Figura.png)
> Hablando por herencia, la clase base o también dicho la clase padre es `Fifura`, donde se derivan las subclases o también llamadas clases hijas como: `Class Circulo`, `Class Rectangulo` y `Class Cuadrado`. 

> Todas estas clases se conectan con la súper clase  `Class Main Program`, incluyendo la clase `Vector2d`, y aunque no lo he mencionado antes, la clase interfaz `IColor` esta conectado con: `Class Circulo`, `Class Rectangulo` y `Class Cuadrado`.  


###Programa de Figura.


    public interface IColor
    {
        void Color(string color);
    }

    class Vector2d
    {
        public int x, y;
        public Vector2d(int x, int y)
        {
            this.x = x; this.y = y;
        }
        public override string ToString()
        {
            return String.Format("{0},{1}", x, y);
        }
    }
    abstract class Figura
    {
        public Vector2d position;
        public string fill, border;

        
        public Figura() : this(new Vector2d(100, 100))
        {

        }
        public Figura ()
        {
            Console.WriteLine("Esta es una figura no definida");
        }
        
        public Figura(Vector2d pos)
        {
            position = pos;
            fill = "white";
            border = "black";
        }
        public virtual abstract void Dibuja();
    }

    class Circulo : Figura, IColor
    {
        private int radio;
        public Circulo(Vector2d pos, int radio) : base(pos)
        {
            this.radio = radio;
        }
        public Circulo() : base()
        {
            this.radio = 10;
        }
        public Circulo ()
            {
            Console.WriteLine("Este es un circulo");
            }
         void IColor.Color(string color) 
        {
            Console.WriteLine("{0} es el color escogido", color);
        }

        public override void Dibuja()
        {
            Console.WriteLine("Se dibuja un circulo en {0} de color {1}", position, fill);
        }
    }

    class Rectangulo : Figura, IColor
    {

        public Rectangulo(Vector2d pos) : base(pos)
        {

        }
        public Rectangulo() : base()
        {

        }
        public Rectangulo ()
        {
            Console.WriteLine("Esta es la figura de rectangulo");
        }
        void IColor.Color(string color)
        {
            Console.WriteLine("El color tomado es el {0}", color);
        }

        public override void Dibuja()
        {
            Console.WriteLine("Se dibuja un Rectangulo en {0} de color {1}", position, fill);
        }
    }

    abstract class Cuadrado : Figura, IColor
    {

        public Cuadrado(Vector2d pos) : base(pos)
        {

        }
        public Cuadrado() : base()
        {

        }
        public Cuadrado ()
        {
            Console.WriteLine("Este es un cuadrado");
        }
        void IColor.Color(string color)
        {
            Console.WriteLine("El color tomado es el {0}", color);
        }
        public override void Dibuja()
        {
            Console.WriteLine("Aqui se dibuja de diferente maneta");
        }
    }
        class Program
    {
        static void Main(string[] args)
        {

            List<Figura> figuras = new List<Figura>();
            figuras.Add(new Circulo());
            figuras.Add(item: new Cuadrado());
            figuras.Add(new Rectangulo(new Vector2d(200, 200)));
            foreach (Figura f in figuras)
            f.Dibuja();

        }

    }


### Base.
La palabra `Base` nos sirve para reutilizar código ya existente en otra clase,  por medio de una herencia. Aparte si el código se llegara a escribir dos o más veces, marcaría error por no reutilizar el código.

Por eso la palabra `Base` es muy utilizada en C# en constructores por medio de herencias para reutilizar los códigos.  