# InnLibrary
Creat by : Денис Казанцев & Артем Николаев

-lib

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    
    namespace InnLibrary
    {
        public class CheckInn
        {
            public static bool CorrectFillINN(string innCode)
            {
                if (string.IsNullOrWhiteSpace(innCode))
                {
                    return false;
                }
                int rez = 0;
                int rez1;
                int zer = 0;
                int zer1;
                int[] z = new int[] { 7, 2, 4, 10, 3, 5, 9, 4, 6, 8 };
                int[] zz = new int[] { 3, 7, 2, 4, 10, 3, 5, 9, 4, 6, 8 };
                int zLenght = z.Length;
                int zzLenght = zz.Length;
                char[] mas = innCode.ToCharArray();
                for (int i = 0; i < zLenght; i++)
                {
                    string asd = mas[i].ToString();
                    rez1 = z[i] * int.Parse(asd);
                    rez = rez + rez1;
                }
                for (int ii = 0; ii < zzLenght; ii++)
                {
                    string asd = mas[ii].ToString();
                    zer1 = zz[ii] * int.Parse(asd);
                    zer = zer + zer1;
                }
                int pred = int.Parse(mas[mas.Length - 2].ToString());
                int pred2 = int.Parse(mas[mas.Length - 1].ToString());
                int chislo1 = rez / 11;
                int chika = rez % 11;
                int chika2 = zer % 11;
                int chislo2 = zer / 11;
                int zxc = 11 * chislo1 + pred;
                int zxc2 = 11 * chislo2 + pred2;
    
                if (chika < 9)
                {
                    chika = chika % 10;
                }
                if (chika2 > 9)
                {
                    chika2 = chika2 % 10;
    
                }
                Console.WriteLine(chika + " " + chika2);
                if (zxc == rez || zxc2 == zer)
                {
                    if (chika == pred || chika2 == pred2)
                    {
                        return true;
                    }
                    else
                    {
                        return false;
                    }
                }
                else
                {
                    return false;
                }
            }
        }
    }


-tests


    using Microsoft.VisualStudio.TestTools.UnitTesting;
    using System;
    using InnLibrary;
    
    namespace InnLibraryTests
    {
        [TestClass]
        public class CheckInnTest
        {
            [TestMethod]
            public void InnTest_1()
            {
                //Arrange
                string innCode = "825002039663";
                //Act
                bool exeptin = CheckInn.CorrectFillINN(innCode);
                //Assert
                Assert.IsTrue(exeptin);
            }
            [TestMethod]
            public void InnTest_2()
            {
                //Arrange
                string innCode = "663555067806";
                //Act
                bool exeptin = CheckInn.CorrectFillINN(innCode);
                //Assert
                Assert.IsTrue(exeptin);
            }
            [TestMethod]
            public void InnTest_3()
            {
                //Arrange
                string innCode = "128808228380";
                //Act
                bool exeptin = CheckInn.CorrectFillINN(innCode);
                //Assert
                Assert.IsTrue(exeptin);
            }
            [TestMethod]
            public void InnTest_4()
            {
                //Arrange
                string innCode = "454510869905";
                //Act
                bool exeptin = CheckInn.CorrectFillINN(innCode);
                //Assert
                Assert.IsTrue(exeptin);
            }
            [TestMethod]
            public void InnTest_5()
            {
                //Arrange
                string innCode = "112107486650";
                //Act
                bool exeptin = CheckInn.CorrectFillINN(innCode);
                //Assert
                Assert.IsTrue(exeptin);
            }
            [TestMethod]
            public void InnTest_6()
            {
                //Arrange
                string innCode = "996581708551";
                //Act
                bool exeptin = CheckInn.CorrectFillINN(innCode);
                //Assert
                Assert.IsTrue(exeptin);
            }
            [TestMethod]
            public void InnTest_NullOrEmpty()
            {
                //Arrange
                string innCode = " ";
                //Act
                bool exeptin = CheckInn.CorrectFillINN(innCode);
                //Assert
                Assert.IsFalse(exeptin);
            }
        }
    }

