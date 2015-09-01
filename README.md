using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
	// Get the stack [See above definition of this method]
	Stack<int> stack = GetStack();

	// Pop the top element
	int pop = stack.Pop();

	// Write to the console
	Console.WriteLine("--- Element popped from top of Stack ---");
	Console.WriteLine(pop);

	// Now look at the top element
	int peek = stack.Peek();
	Console.WriteLine("--- Element now at the top ---");
	Console.WriteLine(peek);
    }
}
----a screen to insert elements into a stack

namespace TestApp
{
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();

    }

    private void Form1_Load(object sender, EventArgs e)
    {
        listBox1.Items.Add("First Name");
        listBox1.Items.Add("Last Name");
        listBox1.Items.Add("Phone");
    }

    private void listBox1_MouseDown(object sender, MouseEventArgs e)
    {
        ListBox box = (ListBox)sender;
        String selectedValue = box.Text;
        DoDragDrop(selectedValue.ToString(), DragDropEffects.Copy);
    }

    private void panel1_DragEnter(object sender, DragEventArgs e)
    {
        if (e.Data.GetDataPresent(DataFormats.Text))
        {
            e.Effect = DragDropEffects.Copy;
        }
        else
        {
            e.Effect = DragDropEffects.None;
        }
    }

    private void panel1_DragDrop(object sender, DragEventArgs e)
    {
        Label newLabel = new Label();
        newLabel.Name = "testLabel";
        newLabel.Text = e.Data.GetData(DataFormats.Text).ToString();

        //Do I need to call either of the following code to make it do this?
        newLabel.Visible = true;
        newLabel.Show();

        panel1.Container.Add(newLabel);
    }
}

--- a screen to remove the elements into stack

using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
	// Get the stack [See method definition above]
	Stack<int> stack = GetStack();

	// Count the number of elements in the Stack
	int count = stack.Count;
	Console.WriteLine("--- Element count ---");
	Console.WriteLine(count);

	// Clear the Stack
	stack.Clear();
	Console.WriteLine("--- Stack was cleared ---");
	Console.WriteLine(stack.Count);
    }
}

---a screen to show all current elements in the stack

void detectScreenType()
    {
        double dpi = DisplayProperties.LogicalDpi;
        var bounds = Window.Current.Bounds;
        double h;
        switch (ApplicationView.Value)
        {
            case ApplicationViewState.Filled:
                h = bounds.Height;
                break;

            case ApplicationViewState.FullScreenLandscape:
                h = bounds.Height;
                break;

            case ApplicationViewState.Snapped:
                h = bounds.Height;
                break;

            case ApplicationViewState.FullScreenPortrait:
                h = bounds.Width;
                break;

            default:
                return;
        }
        double inches = h / dpi ;
        string screenType = "Slate";
        if (inches < 10)
        {
            screenType = "Slate";
        } else if (inches < 14) {
            screenType = "WorkHorsePC";
        }
        else 
        {
            screenType = "FamilyHub";
        }
        ApplicationDataContainer localSettings = Windows.Storage.ApplicationData.Current.LocalSettings;
        localSettings.Values["screenType"] = screenType;
    }
