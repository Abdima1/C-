using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Data.SqlClient;

namespace PatientsRecord
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void insertbtn_Click(object sender, EventArgs e)
        {
            SqlConnection con = new SqlConnection("Data Source=DESKTOP-NVIG551\\SQLEXPRESS;Initial Catalog=dummy_database;Integrated Security=True");
            con.Open();
 SqlCommand cmd = new SqlCommand("insert into patients_details_table(patients_id,paients_first_name,paients_last_name,paients_DoB,patients_Address,patients_City,patients_county,patients_admittedby,patinets_attendedby) " +
         "values('"+pidtext.Text+"','"+ fnametxt.Text+ "','"+lnametxt.Text + "','"+ dobtextBox1 .Text+"','"+ addresstxt.Text+ "','"+ citytxt.Text +"','"+ countytxt.Text + "','"+ admitteddatxt.Text+"','"+ attendedtxt.Text+ "')",con);
            cmd.ExecuteNonQuery();
            con.Close();


            /*Once we have loaded the data inside our database we need to come and 
             and clear the the fields for more data enry*/
            pidtext.Clear();
            fnametxt.Clear();
            lnametxt.Clear();
            dobtextBox1.Clear();
            addresstxt.Clear();
            citytxt.Clear();
            countytxt.Clear();
            admitteddatxt.Clear();
            attendedtxt.Clear();
        }
    }
}
