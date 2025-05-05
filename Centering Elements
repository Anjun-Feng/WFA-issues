# Centering elements

Here's an example of centering a pictureBox. You **MUST** create the events first in the designer!

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Diagnostics;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace blockCode_starter
{
    public partial class Form1 : Form
    {

        public Form1()
        {
            InitializeComponent();
        }

 
        private void CenterPictureBox()
        {
            if (pbWhenClicked != null )
            {
                // Prevent potential issues during minimize/maximize events
                if (this.WindowState == FormWindowState.Normal || this.WindowState == FormWindowState.Maximized)
                {
                    pbWhenClicked.Location = new Point(
                        this.ClientSize.Width / 2 - pbWhenClicked.Width / 2,
                        this.ClientSize.Height / 2 - pbWhenClicked.Height / 2);
                }
            }
        }

        private void Form1_SizeChanged(object sender, EventArgs e)
        {
            CenterPictureBox(); // Re-center whenever the form size changes
            Debug.WriteLine("1");
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            CenterPictureBox(); // Center initially
        }
    }
}

```
