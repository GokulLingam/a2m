# a2m
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Runtime.InteropServices;


namespace A2M
{
	public partial class Form1 : Form
	{
		public Form1()
		{
			InitializeComponent();
		}

		private void flowLayoutPanel1_Paint(object sender, PaintEventArgs e)
		{

		}

		private void label1_Click(object sender, EventArgs e)
		{

		}

		private void Form1_Load(object sender, EventArgs e)
		{

		}

		private void label1_Click_1(object sender, EventArgs e)
		{

		}

		private void button1_Click(object sender, EventArgs e)
		{

			string folder1 = this.textBox1.Text;
			int counter = 0,temp,i, start = 0,s,l;
			string line,ans;

			Console.Write("Input your search text: ");
			string text =".scl" ;
			
			System.IO.StreamReader file =
				new System.IO.StreamReader("C:\\Users\\gokul\\OneDrive\\Desktop\\file.a2m");

			while ((line = file.ReadLine()) != null)
			{



				while ((start < line.Length)&&(temp = line.IndexOf(".scl", start)) != -1)
				{

					for (i = temp; i > -1 && line[i] != ' '; i--) ;
					s = i + 1;
					l = temp + 4 - s;
					//ans = line.Substring(i+1, temp+3);
					this.textBox2.Text = line.Substring(s,l);
					start = temp + 4;
				}
				break;
				if (line.Contains(text))
				{
					counter++;
				
				}

				
			}


			

			file.Close();

			Console.ReadLine();
		}
		private void xlsheet()
		{
			Excel.Application xlApp = new Microsoft.Office.Interop.Excel.Application();

			if (xlApp == null)
			{
				MessageBox.Show("Excel is not properly installed!!");
				return;
			}


			Excel.Workbook xlWorkBook;
			Excel.Worksheet xlWorkSheet;
			object misValue = System.Reflection.Missing.Value;

			xlWorkBook = xlApp.Workbooks.Add(misValue);
			xlWorkSheet = (Excel.Worksheet)xlWorkBook.Worksheets.get_Item(1);

			xlWorkSheet.Cells[1, 1] = "ID";
			xlWorkSheet.Cells[1, 2] = "Name";
			xlWorkSheet.Cells[2, 1] = "1";
			xlWorkSheet.Cells[2, 2] = "One";
			xlWorkSheet.Cells[3, 1] = "2";
			xlWorkSheet.Cells[3, 2] = "Two";



			xlWorkBook.SaveAs("d:\\csharp-Excel.xls", Excel.XlFileFormat.xlWorkbookNormal, misValue, misValue, misValue, misValue, Excel.XlSaveAsAccessMode.xlExclusive, misValue, misValue, misValue, misValue, misValue);
			xlWorkBook.Close(true, misValue, misValue);
			xlApp.Quit();

			Marshal.ReleaseComObject(xlWorkSheet);
			Marshal.ReleaseComObject(xlWorkBook);
			Marshal.ReleaseComObject(xlApp);

			MessageBox.Show("Excel file created , you can find the file d:\\csharp-Excel.xls");

		}

	}
}
/*while ((temp = line.IndexOf(".scl", 0)) != -1)
				{

					counter++;
				for (i = temp; i>0  && line[i] !=' ' ; i--) ;

				ans = line.Substring(i + 1, temp + 3);
				        temp = line.IndexOf(".scl", 0);
						this.textBox2.Text = ""+temp;
						start = temp + 3;
						
					

				}


				break;*/
