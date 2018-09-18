# Rectangle

using System;
using System.Collections.Generic;
using System.Text;
using System.Threading;

namespace RectangleCalculation
{
    class Program
    {
        static void Main(string[] args)
        {
             try
            {
                
                Console.WriteLine("How many Rectangle do you want to draw? (Maximum 5) Please enter: ");
                int numThreads = Convert.ToInt32(Console.ReadLine());
                int[] ArrHight = new int[numThreads];
                int[] ArrWidth = new int[numThreads];
                bool EnterNumeric = true;
                if (numThreads <= 5)
                {
                    for (int i = 0; i < numThreads; i++)
                    {

                        try
                        {
                            int j = i + 1;
                            Console.Write("\n Rectangle : " + j.ToString() + "\n");

                            Console.Write("Please Enter Hight: ");
                            ArrHight[i] = Convert.ToInt32(Console.ReadLine());

                            Console.Write("Please Enter Width: ");
                            ArrWidth[i] = Convert.ToInt32(Console.ReadLine());

                            EnterNumeric = true;
                            
                        }
                        catch (Exception EX)
                        {
                            Console.WriteLine("Please enter only numeric value for Height and Width.\n");
                            EnterNumeric = false;
                            break;
                            //throw new Exception();
                           

                        }

                    }
                    if (EnterNumeric == true)
                    {
                        for (int i = 0; i < numThreads; i++)
                        {
                            Rectangle Rec = new Rectangle();
                            int j = i + 1;
                            Console.Write("\nOutPut for Rectangle : " + j.ToString() + "\n");
                            Thread thread = new Thread(() => Rec.CalcRectangle(ArrHight[i], ArrWidth[i]));
                            thread.Start();
                            thread.Join();
                        }
                    }
                    Console.WriteLine("Please press enter to exit.");
                    Console.Read();
                }
                else
                {
                    Console.WriteLine("Please enter maximum 5 amount. Please press enter to exit");
                    Console.Read();
                }
            }
            catch (Exception Ex)
            {
                Console.WriteLine("Please enter only numeric value. Please press enter to exit");
                Console.Read();
            }
        

        }
        
    }

}




















using System;
using System.Collections.Generic;
using System.Text;

namespace RectangleCalculation
{
    public class Rectangle
    {
         protected int m_width;
        protected int m_height;

        public void setWidth(int width)
        {
            m_width = width;
        }

        public void setHeight(int height)
        {
            m_height = height;
        }


        public int getWidth()
        {
            return m_width;
        }

        public int getHeight()
        {
            return m_height;
        }

        public int getArea()
        {
            return m_width * m_height;
        }
        public void CalcRectangle(int Height, int Width)
        {
            try
            {
                setHeight(Height);
                setWidth(Width);

                Console.Write("\nRectangle Hight is: " + getHeight());
                Console.Write("\nRectangle Width is: " + getWidth());
                Console.WriteLine("\nRectangle area is : " + getArea());
                
                
            }
            catch (Exception Ex)
            {
                Console.WriteLine("Please enter only numeric value for Hight and Width\n");
            }
        }

    }
}

