# Fix focus issues (adding a global control)

This is how you can fix the focus issue for a `tableLayoutPanel` while there are other elements (e.g., `buttons, lables`)

```csharp
﻿using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.IO;

namespace GridMovement3
{
    public partial class Form1 : Form
    {
        // size of the grid 
        int size = 3;

        // represents the initial position of the character
        int x = 0;
        int y = 2;

        // Create a 2d array of pictureBoxes to simulate our grid
        PictureBox[,] pictures = new PictureBox[3, 3];

        // path to our images
        string path_to_pacman = Directory.GetCurrentDirectory() + "/Images/pacman.png";
        string path_to_ghost = Directory.GetCurrentDirectory() + "/Images/ghost.png";
        
        public Form1()
        {
            InitializeComponent();

            // traverse the elements in pictures (i.e., our grid)
            for (int i = 0; i < size; i++)
            {
                for (int j = 0; j < size; j++)
                {
                    // initialize each cell by background image
                    pictures[i, j] = new PictureBox();
                    pictures[i, j].Image = Image.FromFile(path_to_ghost);
                    pictures[i, j].SizeMode = PictureBoxSizeMode.StretchImage;
                    
                    tableLayoutPanel1.Controls.Add(pictures[i, j]);
                }
            }

            // set the initial position of the character
            pictures[y, x].Image = Image.FromFile(path_to_pacman);
        }

        protected override bool ProcessCmdKey(ref Message msg, Keys keyData)
        {
            switch (keyData)
            {
                case Keys.Right:
                    MovePacman(1, 0);
                    return true;
                case Keys.Left:
                    MovePacman(-1, 0);
                    return true;
                case Keys.Up:
                    MovePacman(0, -1);
                    return true;
                case Keys.Down:
                    MovePacman(0, 1);
                    return true;
            }
            return base.ProcessCmdKey(ref msg, keyData);
        }

        private void MovePacman(int dx, int dy)
        {
            int newX = x + dx;
            int newY = y + dy;

            if (newX >= 0 && newX < size && newY >= 0 && newY < size)
            {
                pictures[y, x].Image = Image.FromFile(path_to_ghost);
                x = newX;
                y = newY;
                pictures[y, x].Image = Image.FromFile(path_to_pacman);
            }
        }

        private void Form1_KeyDown(object sender, KeyEventArgs e)
        {

        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }
    }
}
```
