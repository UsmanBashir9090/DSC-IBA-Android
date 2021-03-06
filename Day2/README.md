# DSC-IBA | Android Bootcamp

# Day 2 (XML and Layouts)

By Usman Bashir, Core Team member and Android lead @ DSC-IBA

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/frontImage.png)

# Front End: 

From the project panel go to app -> res -> layout and open **activity_main.xml**.
![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/Opening%20main%20xml.png)


The activity_main.xml file is our front end layout file. This is where the designing of the application is done.
To view how your code will look on the screen, choose **split** view. This will reflect your code on to a virtual screen in real-time.

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/code%20and%20design%20split.png)

Make sure that the ViewGroup of your XML file is **Constraint Layout**.
![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/choosing%20viewgroup%20as%20constraint%20layout.png)

## Creating Views

We can now create our own Views like TextView, EditText or Buttons.
### Add TextView
To create a textView
```
<TextView
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
  android:text="Hello World!"/>
```
By doing this, we are creating an empty TextView, which will have the height and width as that of the content it holds. Then we define the text as "Hello World".

After creation of our TextView, we will be able to see "Hello World!" on our virtual screen on the right. 

Next, we add more attributes to our TextView to add style.
```
    <TextView
        android:id="@+id/hello"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="28dp"
        android:text="Hello World!"
        android:textColor="@color/black"
        android:textSize="15dp"/>
        
```
Since this is a constraint view we must define the constraints of the TextView. To define a view's position in ConstraintLayout, you must add at least one horizontal and one vertical constraint for the view. Each constraint represents a connection or alignment to another view or the the parent layout.
In this case, we have no other view, so we add vertical constraints with the parent layout.

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/addingConstraints.png)

Rename the text of the TextView to "First Name" by:
> android:text="First Name"

### Add Button
To add a button to our layout we simply use the following code.
```
 <Button
        android:id="@+id/myButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:backgroundTint="@android:color/background_dark"
        android:text="Press me"/>
        
```
Again, we have created an empty button which will contain the text "Press me". This time however, we have added and extra line: 
> android:id=@+id/myButton

This provides a name to the button which can later be used to identify this particular button. We will pick this up later.

Similar to how we connected the textView to the constraints, we will add constraints to the button as well. However, the top constraint of our button will be connected to the buttom of TextView (Hello World!).

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/addButton.png)

### Add EditText

Next we add an EditText view. 

```
<EditText
        android:id="@+id/firstName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
```

Notice here, that we have given this view an Id as well. The purpose is the same, to be able to identify this view later.
You will also notice that the layout_width is "match_parent" and not "wrap_content". This is to provide more input space to the user. If we used wrap_content instead, the input field would only increase, as the user inputs the values.
![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/addEditText1.png)

Our EditText field is not looking very good at the moment. Lets add some styling and constraints to it.

First we add top constraint to the top of the parent View. I set the bottom constraint of this EditText with the top of the button. You can set this however you like it. Similarly, the left constraint with the left of the parent view and right constraint with the right of the parent view. 


Next, hop over to the design panel from the top right of your screen.
The boxes shows by the yellow area are where horizontal constraints can be customised. Meaning?
Adding for e.g. 20dp will create a margin of 20dp from the parent layout.


![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/constraintsEditText.png)


Our layout design is slowly coming alive!

We now add one more TextView "Last Name". 

We add similar constraints as that of **First Name**.
```
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="28dp"
        android:text="Last Name"
        android:textColor="@color/black"

        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.456" />

```
We create add a margin to the text view with the line:
> android:layout_marginStart="28dp"


![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/addLastName.png)

Next add one last EditText to create an input field for Last Name.
Set the top constraint of this EditText to the bottom of the previous EditText. This will maintain a uniform distance between the views.
```

    <EditText
        android:id="@+id/lastName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="130dp"
        android:layout_marginRight="50dp"


        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.726"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/firstName"
        app:layout_constraintVertical_bias="0.129" />

```

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/EditText2.png)

And there you go! Our front end layout is complete.

# Run App

We now Run the app to see how it appears on our mobile device. 
To run an app, choose the device you want to run it on and then press the play icon beside it.

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/checkResults.png)


# Back End:

We now declare a button variable and 2 EditText variables with respect to our front end layout.

To move to the backend layout go to project panel on the left and then **app -> src -> main -> java -> com -> example -> YourApplicationName -> MainActivity**.
![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/gotoBackend.png)

Next we declare the variables under the public class, but above the onCreate method.
```
Button pressME;
EditText firstName;
EditText lastName;
```

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/declareVariables.png)


Next, in the **onCreate** method, we initialise these variables.
```
  pressMe = findViewById(R.id.myButton);
  firstName = (EditText) findViewById(R.id.firstName);
  lastName = (EditText) findViewById(R.id.lastName);

```

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/initialiseVariables.png)

Great!

Now we move on to adding functions to our front end. What happens when a user pressed the button?

In this tutorial, we want the first name and the last name to be displayed on the app whenever the button is pressed.
For displaying the name, we use a toast. Toasts display information for a short period of time, and then disappear.

We first create an onClick Method for the button
```
pressMe.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
            }
        });
```

When writing View.OnClickListener, press enter on the provided hint by the IDE to automatically create this method.

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/setOnClickListener.png)


Next we add a toast in the following way:


![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/chooseCorrectToast.png)

We want our toast to display the names given to us as input in the form. Therefore in the 'text: ""' we add our EditText variables in the string format.

>  Toast.makeText(MainActivity.this, "Name is " + firstName.getText().toString() +" - " + lastName.getText().toString(), Toast.LENGTH_SHORT).show();
    
First we added a 'Name is ' String. Next we concatenate with it, the string input we have recevied in our editText "First Name". We do this by 'firstName.getText().toString()'. 

We do the same for the last name.

![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/completingToast.png)

Perfect!

We have now created our own front-end layout and connected it to the backend as well.
Lets now run the application and check how we've done.


![alt-text](https://github.com/UsmanBashir9090/DSC-IBA-Android/blob/main/Day2/testRunActivity.png)


## Congratulations!
















