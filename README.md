# DanceContactTracker
This was the first application I wrote after I started learning how to code. It was built in C# as a click once application. In Vero Beach FL there is a dance studio that wanted a rewards system. What is kind of impressive is that they still use this application. 
The coding pretty weak, but I keep it around because this was the application that helped me decide what I wanted to do with my future computer science degree. 
## Application
This is the home screen of the application. </br>
![image](https://user-images.githubusercontent.com/93277335/149252941-5835a63f-b46e-468c-b455-b6c9410a8ced.png)
 

When you load a contact it will bring up their information and show their punches
 ![image](https://user-images.githubusercontent.com/93277335/149252959-4b2bd15c-30f2-4393-bb51-0e6e0d9cce2f.png)


The contacts would buy dances, then use them until they no longer have punches left. If they are attending more than one group dance lesson on the same day it only counts as half a punch. 
 ![image](https://user-images.githubusercontent.com/93277335/149252973-bda8addc-8f62-4a8d-93c0-5b76bd034171.png)

Once they reach 1 punch, it alerts the instructors that they are low on punches
 ![image](https://user-images.githubusercontent.com/93277335/149252984-1c72ede4-1b73-45af-8711-7616bc9238dd.png)

It will also email the customers to let them know when they are low on punches. 

## Code
This was back before I understood anything about panels or window list. The interesting thing is, I coded the visit and purchase list independently. 
```c#
//Build Punch Card

private void AddPunchInstancePanel(int index)

{

//Create new stuff.

DynaPanel punchInstancePanel = new DynaPanel(index);

DynaLabel punchInstanceNumber = new DynaLabel(index);

DynaTextBox punchInstanceDateBox = new DynaTextBox(index);

DynaButton punchInstanceDelButton = new DynaButton(index);



//Index Number

punchInstanceNumber.AutoSize = true;

punchInstanceNumber.Location = new System.Drawing.Point(3, 6);

punchInstanceNumber.Name = punInstNumName;

punchInstanceNumber.Size = new System.Drawing.Size(16, 13);

//punchInstanceNumber.TabIndex = index + 1;

punchInstanceNumber.Text = index + 1 + ":";



//Date Box

punchInstanceDateBox.Location = new System.Drawing.Point(38, 3);

punchInstanceDateBox.Name = punInstDateName;

punchInstanceDateBox.TextAlign = HorizontalAlignment.Center;

punchInstanceDateBox.Size = new System.Drawing.Size(72, 20);

punchInstanceDateBox.TabIndex = index * 3 + 1;

punchInstanceDateBox.Text = "";

punchInstanceDateBox.BackColor = Color.White; //Leaving this here so I can edit later. I want it to turn Yellow when half punch.

punchInstanceDateBox.Enter += new EventHandler(punchInstanceDateBox_Enter);

punchInstanceDateBox.Leave += new EventHandler(punchInstanceDateBox_Leave);

punchInstanceDateBox.KeyPress += new KeyPressEventHandler(punchInstanceDateBox_KeyPress);



//Delete Button

punchInstanceDelButton.Location = new System.Drawing.Point(116, 1);

punchInstanceDelButton.Name = punInstDelName;

punchInstanceDelButton.Size = new System.Drawing.Size(32, 23);

punchInstanceDelButton.TabIndex = index * 3 + 2;

punchInstanceDelButton.Text = "Del";

punchInstanceDelButton.UseVisualStyleBackColor = true;

punchInstanceDelButton.Click += new EventHandler(PunchInstanceDelButton_Click);



//Instance Panel

punchInstancePanel.Controls.Add(punchInstanceDelButton);

punchInstancePanel.Controls.Add(punchInstanceNumber);

punchInstancePanel.Controls.Add(punchInstanceDateBox);

punchInstancePanel.Location = new System.Drawing.Point(3, 2 + (punchInstanceHeight * index));

punchInstancePanel.Name = "punchInstancePanel";

punchInstancePanel.Size = new System.Drawing.Size(153, 26);

//punchInstancePanel.TabIndex = index + 1;



datePanel.Controls.Add(punchInstancePanel);

}
```


