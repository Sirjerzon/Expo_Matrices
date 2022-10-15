using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;

namespace Exposicion
{

    public class Program
    {
        public static void Main()
        {

            int opc = 0;
            StreamWriter writer = null;
          
            do
            {
                Console.Clear();
                Console.WriteLine("tablas de multiplicar del 1 al 9");
                Console.WriteLine("-----------------------");
                Console.WriteLine("1. CREAR ARCHIVO");
                Console.WriteLine("2. ESCRIBIR");
                Console.WriteLine("3. LEER");
                Console.WriteLine("4. Mostrar tablas");
                Console.WriteLine("5. SALIR");
                Console.WriteLine("-----------------------");
                Console.WriteLine("INGRESE OPCION: ");
                opc = Convert.ToInt32(Console.ReadLine());


                switch (opc)
                {
                    case 1:
                        CreateFile(writer);
                        break;
                    case 2:
                        WriteFile(writer);
                        break;

                    case 3:
                        ReadFile(writer);
                        break;
                    case 4:
                        
                        for (int i = 0; i < 10; i++)
                        {
                            for (int j = 0; j < 10; j++)
                            {
                                if (i == 0)
                                    Console.Write(j + " ");
                                else if (j == 0)
                                    Console.Write(i + " ");
                                else
                                    Console.Write((i * j) + " ");
                            }
                            Console.Write("\n");
                        };
                        
                        break;
                   
                    case 5:
                        Console.WriteLine("gracias!!!");
                        break;
                    default:
                        Console.WriteLine("error, intente de nuevo");
                        break;
                }
                Console.ReadKey();
            } while (opc != 5);
        }
       
        public static void CreateFile(StreamWriter writer)
        {
            writer = new StreamWriter("./matriz.txt");
            writer.Close();
            Console.WriteLine("Archivo Creado :)");
        }
        public static void WriteFile(StreamWriter writer)
        {
            writer = new StreamWriter("./matriz.txt");
            writer.WriteLine(@"
                0 1 2 3 4 5 6 7 8 9
                1 1 2 3 4 5 6 7 8 9
                2 2 4 6 8 10 12 14 16 18
                3 3 6 9 12 15 18 21 24 27
                4 4 8 12 16 20 24 28 32 36
                5 5 10 15 20 25 30 35 40 45
                6 6 12 18 24 30 36 42 48 54
                7 7 14 21 28 35 42 49 56 63
                8 8 16 24 32 40 48 56 64 72
                9 9 18 27 36 45 54 63 72 81
        ");
            writer.Close();

            Console.WriteLine("archivo de texto llenado");
        }
        
        
        public static void ReadFile(StreamWriter writer)
        {
            StreamReader reader = new StreamReader("./matriz.txt");

            do
            {
                Console.WriteLine(reader.ReadLine());
            }
            while (reader.Peek() != -1);

        }
    }
}
