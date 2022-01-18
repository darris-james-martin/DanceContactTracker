# DanceContactTracker
This was the first application I wrote in C# as a Click Once application, after I first began learning how to code. This is a rewards system application that was created in 2012 for a dance studio in Vero Beach, FL. What is kind of impressive is that this application is still in use today without any maintenance.  

It is obvious the code was developed by a novice developer, but I keep it around because this was the application that helped me decide what I wanted to do with my future Computer Science degree.  

## Application
This is the home screen of the application. </br> 
![image](https://user-images.githubusercontent.com/93277335/149252941-5835a63f-b46e-468c-b455-b6c9410a8ced.png) 

When a contact is loaded, it will bring up their information and show their punches.</br> 
![image](https://user-images.githubusercontent.com/93277335/149252959-4b2bd15c-30f2-4393-bb51-0e6e0d9cce2f.png) 

The contacts will buy dances, then use them until no punches remain. If contacts are attending more than one group dance lesson on the same day, it only counts as half a punch. </br> 
![image](https://user-images.githubusercontent.com/93277335/149252973-bda8addc-8f62-4a8d-93c0-5b76bd034171.png) 

Once the contact has 1 punch remaining, it alerts the instructors and the contacts, via email, that they are low on punches.</br> 
![image](https://user-images.githubusercontent.com/93277335/149252984-1c72ede4-1b73-45af-8711-7616bc9238dd.png) 

## Code
Before exploring the proper use of panels and windowlist, I developed the detail items for visits and purchases independently. 
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


