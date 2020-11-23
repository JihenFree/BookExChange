# BookExChange

![Bookex](https://lh3.googleusercontent.com/pw/ACtC-3eL6emsay9aaOlb2jdUfDVRnA8aykkOLQsJdJjVYdTMwQ47lxYjtl6Jvytxi3mi2yl26i0RlQzfp8vq19tnngvOrNNP7SdrV-7lyrYW6NIupdgj8rZZ0uFP-_IJaVd5nH-NgITqTAAX_eS-lrqtYe7C=w666-h148-no)

BookExChange is a web-based application that allows people from all over the world to exchange books freely. It looks like a Used Books Webshop except the fact that the books here are free, as it's not about buying but it's rather about Exchanging.

## Table of content

  * [Why BookExChange ?](#why-bookexchange--)
  * [How does BookExChange Work ?](#how-does-bookexchange-work--)
  * [Built with](#built-with)
  * [Site Structure](#site-structure)
    + [Layout](#layout)
      - [Navigation Bar links for visitors](#navigation-bar-links-for-visitors)
      - [Navigation Bar links for logged in users](#navigation-bar-links-for-logged-in-users)
    + [Home Page](#home-page)
      - [Search for a book](#search-for-a-book)
        * [Search by Category](#search-by-category)
        * [Search by title, author or ISBN](#search-by-title--author-or-isbn)
      - [Book page (for visitors)](#book-page--for-visitors-)
    + [Register](#register)
    + [Log in](#log-in)
    + [Add book](#add-book)
    + [My Books](#my-books)
      - [My profile](#my-profile)
      - [My book page](#my-book-page)
    + [My Wishlist](#my-wishlist)
      - [User's Wishlist](#user-s-wishlist)
    + [Inbox](#inbox)
    + [Get this book](#get-this-book)
      - [Regulated gotten books quota](#regulated-gotten-books-quota)
   - [Developed by](#developed-by)

## Why BookExChange ?

The main concept of BookExChange is sharing. So for anyone who wants to remove few books from their bookshelf to acquire new ones without any selling or buying processes, and in a way that might bring them enjoyable and enriching social experiences, BookExChange is the place to be and the app to use.

## How does BookExChange Work ?

Registered users Add to their profile the books they want to Exchange and every user can send a get request to the owner, by simply clicking the Get button, for the book they want to have. 

Once the owner Sends the book, they have to type in the small form the shipping details and then new owner receives a notification to be informed about it. 

There is a quota that restricts the number of books allowed to be requested. In fact, every user can request only one more book than the total number of books they have given.

Users can also message each other to eventually get acquainted or ask for further information.

Non registered visitors, can also look for books on BookExChange and see users profiles. Exchanges and messages do work only for logged in users, though.

## Built with

* Python
* Flask
* SQLite 
* JavaScript
* jQuery - Ajax
* HTML
* Jinja
* CSS
* [Bootstrap](https://getbootstrap.com/) and [Bootswatch](https://bootswatch.com/sketchy/) theme.

## Site Structure

### Layout

The common view consists of the navigation bar that contains the brand which is also a clickable button that redirects to home page.
All links [Bootstrap](https://getbootstrap.com/) style sheets library as well as JavaScript library, applicable to all templates, are referenced in head of layout.html : 

```HTML
<!-- documentation at http://getbootstrap.com/docs/4.1/, alternative themes at https://bootswatch.com/ -->
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" rel="stylesheet">
<link href="https://bootswatch.com/4/sketchy/bootstrap.min.css" rel="stylesheet">
<link href="https://bootswatch.com/4/sketchy/bootstrap.css" rel="stylesheet">
<link href="https://bootswatch.com/4/sketchy/_variables.scss" rel="stylesheet">
<link href="https://bootswatch.com/4/sketchy/_bootswatch.scss" rel="stylesheet">

<!-- https://favicon.io/emoji-favicons -->
<link rel="icon" type="image/png" sizes="32x32" href="/static/favicon-32x32.png">

<link href="/static/styles.css" rel="stylesheet">
<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js"></script>
```

Depending on whether the user is logged in or not, the navigation links change as follows :
#### Navigation Bar links for visitors 
- Register
- Log in

![Layout1](https://lh3.googleusercontent.com/pw/ACtC-3cET-ekCngA5pxaaQDkyH68hnk6v22Mu4EHazG0GYu2rU2k40X55BhIt8KmAh2wMKSAU3UvhsD-q45_zWj8ZWH10euFm0eAgEuI3cmO887kYVuva4-NwLF_0CS8OPthN2uRjAMkyf5bnnMDlMA4CBbE=w1244-h657-no)


#### Navigation Bar links for logged in users

* Add Book
* My Books
* My Wishlist
* Inbox
* Log out


![Layout2](https://lh3.googleusercontent.com/pw/ACtC-3eGkFiGDIYGHg1AK68JxXYAeqYgFTjUY0gEELL0z2i2Suf3bAflpAFUIz-1BcVd7GhPcSDHKBXjSNfC1noMrOH1iU9Nyz2cYzL-aj_LW4WKpTDXoLOUxv8roapQpT0dP31f-M7JkAb1rux-G3nhqtgr=w1242-h657-no)

### Home Page

Home page is the same for logged in users and visitors (except navigation bar links as described previously). On the upper part, Random books from BookExChange database library are displayed in a row, and so are the books that were Recently added to BookExChange database, in a row below it, using SQL code `ORDER BY datetime DESC` datetime being the date and time when the book was added. Every time The navbar brand is clicked, home page is loaded again and the displayed random books change.  

![Home page](https://lh3.googleusercontent.com/pw/ACtC-3fyZlJIjj9vJy8WnsizTp2NX2mKPQFWcl4HeDmJrEVDW27eESWkBnxWDhDcGRxnqV9msmbqkd5y6VEVt5weQrNweBUf8AP_csmJ9tXX5Ku1EqNfWOa0u8wwrxhfJlWuS_9ty2BfAxVqYz55j4Lc6OHN=w600-h338-no)

#### Search for a book

Home page contains also Search functionality. Either by typing in the search input the title, author or ISBN of the book and then click find, or by choosing a Category from the list in the drop down menu.

##### Search by Category

By clicking the *Category* drop down menu and picking a category in the list, The books from the chosen category, in BookexChange data base, are displayed.

![Search by category](https://lh3.googleusercontent.com/pw/ACtC-3e_VubVTB73vO8AdU_fbWUX1PIIc8fsQlVMemT6T1eS3tgtJCsaD8pHxxNwxkDcaSSrA0DUK9Cgph13xrflGYLbj7NRMuGP0Iwk3xquMeQ7rHEBg8fvaufXtZbual9tmE9CG9dxOq9aqVQJyWtfC7u_=w600-h338-no)

##### Search by title, author or ISBN
The input box for Search by title, author or ISBN offers a list of suggestions from BookexChange database, for the typed string. Everytime the key is pressed, the list of suggestions is updated according to the string in the box.  jQuery’s $.get function is used here:
```HTML
...
 <form action="/" method="get" >
<input class="form-control form-control-lg" size="30"  type="text" name="search" id="search" placeholder="Search by title, author or ISBN" list="booksfound">
      <datalist id="booksfound">
</form>
...
<script>
    let input = document.getElementById("search");
    input.onkeyup = function() {
        $.get('/?q=' + input.value, function(data) {
            document.getElementById("booksfound").innerHTML = data;
        });
 };
 ...
</script>
```
$.get function makes a GET request to the server at the /?q= route, with the value of the string in the input box. Once data received, it is set in the innerHTML of the datalist "booksfound". The Python code in application.py selects from database titles, authors and ISBNs that contain the typed value, and returns search.html template which contains an incomplete fragment of HTML that will be put inside  home.html.
```python
@app.route("/", methods=["GET", "POST"])
def get_index():
...
    # Book search by title or author or ISBN
    if request.args.get("q"):

        term = '%' + request.args.get("q") + '%'
        titles = db.execute("SELECT DISTINCT title FROM Books WHERE title LIKE :word", word=term)
        authors = db.execute("SELECT DISTINCT  author FROM Books WHERE author LIKE :word", word=term)
        isbns = db.execute("SELECT DISTINCT isbn FROM Books WHERE isbn LIKE :word", word=term)
        return render_template("search.html", titles=titles, authors= authors, isbns = isbns)
        ...
```
 The template, search.html, only has <option> elements for the datalist, one for each matching title, author or ISBN.
 ```HTML
{% for title in titles %}
 <option value="{{ title["title"] }}">
{% endfor %}
{% for author in authors %}
<option value="{{ author["author"] }}">
{% endfor %}
{% for isbn in isbns %}
<option value="{{ isbn["isbn"] }}">
{% endfor %}
```
Once the search term typed or picked from the list of suggestions, the user clicks "Find" button to obtain the search result and so the books found are displayed:

![search by title](https://lh3.googleusercontent.com/pw/ACtC-3dAJI7PBUIlXygOsz97JEp-r1homIdANVplZUwDOH0f4RwN6nHk3fJSO0qyP-vQhyPk1iAS8E5i2uGHS6lFqhspdWDLLy76aMc_sVJHhvDUnkhloEMynzhL1uupOdyE6MsADikyxFyOs_tBJ5MWGzY6=w600-h338-no)
#### Book page (for visitors)
Home page allows users as well as visitors to see books details by simply clicking on the book cover photo or title.
Book page contains Cover photo, title of the book and author name which is a clickable link that directs to a page where all books by that author in Bookexchange data base are displayed. Below the author name there are two buttons, *"Get this book"* and *"Add to WishList"* which can be used only by logged in users. We will explain about these bottons later. If a visitor clicks one of these buttons, they will be asked to log in. 
Other information about the book are provided in Book page : Category,  Publisher, Edition, ISBN, Cover type,  book Condition and Faults as all books on Bookexchange are supposed to be used books. There is also Owner's Notes and Book's number in BookexChange as well as date of addition of the book to BookexChange database. Finally, Book's owner which also a clickable link that directs to owner's page.  
![Book page](https://lh3.googleusercontent.com/pw/ACtC-3czmCKB1XynTmj11E_p-QctTzHmWiFHon9L2SQQ-hXlD11uY360Oi1MOS2zarJlaJorcJW-ioz93nChqzAsCsIuetc32jeTPrMFLXKk2vOUm6KxNe06x7bi-HnH4Kb5DXksg01dFblU1hF7wU22cZpb=w600-h338-no)
### Register
Register navbar link allows visitors to become a memeber of Bookexchange community and thus add books to BookexChange database and send book requests to receive the books they were looking for. 
Register page contains following inputs to append new user's information : Username, Password, Password confirmation, Year of birth, and a text area for the user to describe themselves freely. If any one of the inputs is left blank or the username already exists or the password doesn't match the confirmation password, error messages will be displayed and submission will be stopped.
![Register errors](https://lh3.googleusercontent.com/pw/ACtC-3fxiwJtJqs7RbhJl0SHyAZh7lYH2AmpGkhJImOJBkNJMGPSHyHaIuqEj-d4FAmA3wjRQNRZizsQs9V0Id3qtLLJ1l9dAuofYLoxoMZzUXtDRogwM3uNc6r6YOXRxeGIBmAuvexOdNUteOrkYKu5Oxua=w600-h338-no)

Once all fields are filled correctly, New user's information are inserted in users table in bookex database, and it returns Log in page so that new user logs in and sees his profile page. 
![Register submission](https://lh3.googleusercontent.com/pw/ACtC-3dWDqV1gkhQEvSwgJ8nd2eGi7c21g6wKMoapO75r7kEFmwIKEBe44qnHr5F0VBqqs607ol06S74U9Lkb9aYs6VKU1oZ1KriupXX95aYe_HgNpaI36NGQv3G9BhQrbWTT0L7CxlHWetO7-bDoTh2iJnr=w600-h338-no)
### Log in
In Log in page there are two inputs  username and password. Below log in button there is a link  "Create an Account" that returns register page, for visitors that haven't registered yet. If username or password are incorrect an error message appears. 
This is how the error message is processed in */login* app route in *application.py* :
```python
@app.route("/login", methods=["GET", "POST"])
def login():
...
        # Query database for username
        rows = db.execute("SELECT * FROM users WHERE username = :username",
                          username=request.form.get("username"))

        # Ensure username exists and password is correct
        if len(rows) != 1 or not check_password_hash(rows[0]["hash"], request.form.get("password")) or not request.form.get("username") or not request.form.get("password") :
            error = "Invalid username and/or password"
            return render_template("login.html", error=error)
...
```
And this is how the variable *error* placed below the input boxes is passed through *login.html* template with Jinja: 
` <div style="color:red;">{{ error }} </div>`

Once user logged in, home page is returned and user can *log out* by clicking the *Log out* button in navbar.

![login](https://lh3.googleusercontent.com/pw/ACtC-3cnjK0ab5ZEwhvSxJ3qi84jwI3Z_0SpzlnbrYJvjmr-lnGtT_z2uNAq--SF5ym7b97lKiDGOGPs9xGpr5aB8_lTQLt17rjmyMlGmob1IPYjc1lqt52FFqW87LZjjBagvN0zfgJRjoMjGKpyfX9pAAI1=w600-h338-no)

Unlike log in right after registering, usual log in doesn't return profile page template *mybooks.html* which is also accessible by clicking the *My books* button in user navbar (that will be futher explained later) but it returns home page template *home.html*. The choice of template at log in depends on a datum that is altered in database once a newly registred user logs in. That alteration is done in the *index* function in *application.py*. The datum here is *action* in *users* table in bookex database. The value of *action* that is inserted with new user's information at registration is *"add"*. Right after the very first log in, that value is altered to *"no"* so that ater that first log in, home page will be rendered instead of *mybooks.html* :
```python
@app.route("/", methods=["GET", "POST"])
def get_index():
...
        last = db.execute("SELECT * FROM users WHERE id = :userid", userid=session["user_id"])
        head = last[0]["action"]
        db.execute("UPDATE users SET action = :la WHERE id = :idus",
               la='no', idus=session["user_id"])

        if head == "add":
        
            # Render my books when a new book is added or when newly registered or when profile edited
            books = db.execute("SELECT * FROM Books WHERE owner = :userid", userid=session["user_id"])
            owners = db.execute("SELECT * FROM users WHERE id = :ownerid", ownerid=session["user_id"])
            owner = owners[0]
           ...
            return render_template("mybooks.html", books=books, owner=owner, ...)

        else:

            # Display random books  and recently added books in home page for any logged in user
            books = db.execute("SELECT * FROM Books ORDER BY random() LIMIT 6")
            recentbooks = db.execute("SELECT * FROM Books ORDER BY datetime DESC LIMIT 6")
        return render_template("home.html", books=books, recentbooks=recentbooks)
```
Notice that, as mentioned in the comment, *mybooks.html* is rendred the same way right after a new book is added or when user's profile is edited.
### Add book
*Add Book* is the first navbar link from the left in logged in users navbar menu. It calls function *add* from app route */add* in *application.py* which renders template *add.html*. It allows to user to add his books to Bookex database. In *Add Book* page there are inputs for information about the book that have been mentioned previously in Book page paragraph, and which are : 
* Title input.
* Author input : The author input box, like the search input box, offers a drop-down list of suggestions from BookexChange database, containing the typed string. Everytime the key is pressed, the list of suggestions is updated according to the string in the box.  jQuery’s $.get function is used here the same way. This search function is used for *Author* input to avoid name dupilcates for the same author.
* Category drop-down list to select one the categories from the list.

![Add Book](https://lh3.googleusercontent.com/pw/ACtC-3cbln_h_dLysW42eemEr-4mRENXMJ_U5LIto1mKMEyGTXQRiT3Q2A0KUJi-XmNiqqOko2IE2FuQXmlWOZwDDahwRO_AOS4Z0r-lAzo1JNsRSnIg3scwi-Je4QXFRxRjGLNyB_KKSi07UVlbcYOwNxKw=w600-h336-no)
* Publisher input.
* Edition date : it's the date of release of the book's edition.
* ISBN input.
* Cover drop-down list to select the cover type.
* Book Photo : either by *Upload* where user can select a photo file from their computer or by *link* where user can copy and paste url of photo from the web.
* Book Condition : five radio buttons to select a book condition from *As new* to *poor* that corresponds to the actual condition of the book.
* Book faults : check boxes to select several faults like cover creases, bumped corner, stains, etc.
* Notes : textaerea for owner's review or remarks about the book.

If any input is left blank, the script displays an error signal focused on the missing information.

![Add Book error messages](https://lh3.googleusercontent.com/pw/ACtC-3eIB8DpmQZ5H9IlXYTZOgItd2xw76w1QLZVPQY3UA9Ji38mrl7_12J3YaM9gCHJmRWIo_oLJcurDoBv9sCqVaaqqzmWLOli6eQtTa7nK2iP5zvrTIwY8av2ILBHngb83dHru2p-n6d7Qff5pVJnQQQT=w600-h336-no)

Once all required fields are filled and validated, by clicking the *Add* button, information is submitted and inserted into *Books* table in Bookex database then template *mybooks.html* is returned to display updated user's books list to check that the book was successufuly added.

![Add Book submission](https://lh3.googleusercontent.com/pw/ACtC-3c8wKvUjlpnC_lhf6oQ_Ps-odz1vSlwydwdJAZ5RvunZBxbJ0MDZghqNP0zOTbZbDFTz10Wyp1HL6wbODEUmoivLTjad531-yG5u95_OKZ9tf0PPbc_CT249etbP3tXbBTlVMLJNqvLU950FruhT1-r=w600-h336-no)

### My Books

*My Books* navbar link renders template *mybooks.html* which consists of two parts : on top, user's profile information in a card style; and, below it, user's books entiteled *My Books*.

#### My profile

It is the card style yellowish orange rectangle on top of *main* that displays user's information appended in registration : username, age, country and user's description of themself. At he bottom on the card, there is an *Edit my profile* button which renders template *editprofile.html* that allows user to change their information as well as their username and password. If new typed username already exists, an error message is displayed and submission is prevented. All values of unchanged fields remain the same.

![Edit profile](https://lh3.googleusercontent.com/pw/ACtC-3enIP6f6ZmH8HTPhyrO09QFw3-Tn4032DCMmB7H_-kmC9H-L7tzuHGY65MyM25Spc4gtC4RyHTSmVsLx7mMwTAsTzm4HlDcgWGjjuiLY0i6BBjNbVqWiZGk4Ip2tiMoffTTasHsu2tjPEJRrE2qvRfr=w600-h336-no)

#### My book page

Users access their book page by clicking on any book of their own from *My Books* page. Both the cover and the title of the book in the card style book miniature, are links that render the template *mybook.html*. My book page is the same as book page described previously except the buttons below the author name which are here three buttons : 
* Edit : it allows user to modify book's information. *Edit* button renders template *editbook.html* which allows user to alter any data value except the title of the book.
![Edit book](https://lh3.googleusercontent.com/pw/ACtC-3cXGr3_kse0P_bErvjJFB_5zdTIqqtd1_gl5BX-Z8Rgjs9kauaBiTQUxn0-2v-pVKcedn0OYYRGdS0ioi4txZsyqEVM-L9ZqhqI5ZoT_ayfF0jU8VWANsnBziYmbzBSjYgUm_QtSwXuWM_FThJyCZ6X=w600-h336-no)

* Delete  : it allows user to delete a book of his own. When *Delete* button is clicked and alert message is diplayed to confirm the user is sure sure they want to remove the book. Once *Yes* is clicked, Book is deleted from Bookex database and it returns template *mybooks.html* to display the updated user's book table.

![Delete book](https://lh3.googleusercontent.com/pw/ACtC-3fV1Y8UGod2P1IsgpgYSWMnIYMgjeojI0rzfojZYcqyzudlJK27AHDqF-h6JHWsyikdKSXx9ky2Vi_YUUJDu0evojTvc_BVyb2uWMtnF1UyK-sWqE_F-_7outR50aXMbZtuRL9xCyoQcW2CJOvNFaR1=w600-h336-no)

* Hide : it allows the user to make invisible to other users, a book of his own. If the user doesn't want to receive a request for a particular book of his, they just activate the *Hide* botton which is white with yellow outline when the book is visible and becomes *Unhide* and plain yellow when the book is hidden. To make the book visible and accessible again, the user only has to click the same button when it is on *Unhide* position.

![Hide book](https://lh3.googleusercontent.com/pw/ACtC-3egfTnpeb-AOPK99oA-wpnyEKSOTAa34Er6r9OaqMoOLLWdGW6yBZDWY6JQHwwTJnsbyIyF6bqYgRNPmrB_cFJDTBrtmdpSI2jhaSKEMfqBypLSJAvp7lYXnFGT3XbAQ9UHdqWNP4JxispNyJun2O91=w600-h336-no)

jQuery’s $.get function is used here when the *Hide* or *Unhide* button is clicked :
```HTML
...
 <button type="button" id="hide" class="btn btn-outline-warning" onclick="hideFunction()">Hide</button>
<input type="hidden" id="hiddenbook" value="{{ book["hidden"] }}">

 <script>
let input = document.getElementById("bookid");
 if (document.getElementById("hiddenbook").value == "yes")
 {
   document.getElementById("hide").innerHTML = "Unhide";
   document.getElementById("hide").className = "btn btn-warning";
 }
function hideFunction(){
 if (document.getElementById("hiddenbook").value == "no")
 {
  $.get('/hidebook?bookn=' + input.value, function(data) {
        if (data == true) {
          document.getElementById("hide").innerHTML = "Unhide";
          document.getElementById("hide").className = "btn btn-warning";
          document.getElementById("hiddenbook").value = "yes";
        }
    });
 }
  if (document.getElementById("hiddenbook").value == "yes")
 {
  $.get('/unhidebook?bookn=' + input.value, function(data) {
        if (data == true) {
          document.getElementById("hide").innerHTML = "Hide";
          document.getElementById("hide").className = "btn btn-outline-warning";
          document.getElementById("hiddenbook").value = "no"
        }
    });
 }
}
</script>
```

In application.py, under app routes */hidebook* and */Unhidebook* the correspondant value of *hidden*  in *Books* table is altered :
```python
@app.route("/hidebook", methods=["GET", "POST"])
@login_required
def hidebook():
    """Hide a book"""
    if request.args.get("bookn") != "" :

        db.execute("UPDATE Books SET hidden = :hi WHERE owner = :idus AND bookid = :bki",
               hi='yes', idus=session["user_id"], bki=request.args.get("bookn"))
        hidden = True
    return jsonify(hidden)

@app.route("/unhidebook", methods=["GET", "POST"])
@login_required
def unhidebook():
    """UnHide a book"""
    if request.args.get("bookn") != "" :

        db.execute("UPDATE Books SET hidden = :hi WHERE owner = :idus",
               hi='no', idus=session["user_id"])
        unhidden = True
    return jsonify(unhidden)
```

### My Wishlist

*My Wishlist* navbar link displays the books that the user would like to get. A book is added to the wishlist everytime the user clicks the *Add to wishlist <3* button in book page if the book isn't in their Wishlist already, otherwise, it removes it from their Whishlist. The Wishlist button works nearly the same way as the *Hide* button. When a book isn't in user's Whishlist the botton is White wieh yellow outline and says *Add to wishlist <3*; Once the button is clicked, it becomes plain yellow and says *Added to Whishlist <3*, the book is then inserted into *whishlists* table and so it appears in user's Whishlist, to remove the book from their Whishlist, they only have to click the button again.

![Wishlist](https://lh3.googleusercontent.com/pw/ACtC-3cgO0vaAT9vSqblgBKH8irseydLc-zMQO_joMcXYNK6-nLz1sLULIzxSjYkqvxvTvPVZQi7g5d1Zg-6-lIpUdtnB6MDwHi89EXugxuWukpdqUy8CZZXQBAF8H-Y1dvFA0wKwYPHZHpyHSVt1RfHVAsA=w600-h336-no)

#### User's Wishlist

Any user's wishlist is visible by all users and visitors via their profile page, by clicking the button *[username]'s Wishlist*.

![user's Wishlist](https://lh3.googleusercontent.com/pw/ACtC-3ebHxyo8O4hcg886LPyQv_Gtxajt5lWXwBUFBGX4Y37y5hOHbs59HMcVGu9mnHs6_P_cOGfiPMCKpdzuZuxhoIs6ol6McepVnRu58jmZpvkzWujqok9k-2qMDmYpRaZGYviuumyy9da5P98iPh7N-wy=w600-h336-no)

### Inbox

*Inbox* navbar link allows user to check received messages from other users and notifications about books requests. It renders template *inbox.html* which displays the list of messages and notifications in a table containing information about *Sender*, *Object* and *Date* of each message. Unread messages are higlighted in blue and unread notifications are highlighted in yellow.
*Inbox* navbar link has got a red badge that shows the number of unread messages and notifications, it appears only if there are any. $get is used here to return in Json format via get method in route app */unread* in *application.py* the number of unread messages :

```HTML
...
 <li class="nav-item"><a class="nav-link" href="/inbox"><span class="yellow2">Inbox</span>&nbsp;<span id="badge" class="badge badge-pill badge-danger"></span></a></li>
<script>
    var x = "no";
    $.get('/unread?q=' + x, function(data) {
        if (data == 0) {
  document.getElementById("badge").innerHTML = "";
    } else {
      document.getElementById("badge").innerHTML = data;
    }
        });
</script>
...
```
```python
@app.route("/unread", methods=["GET"])
def unread():
    """Return  in JSON format"""
    t = request.args.get("q")
    # Query database
    rows = db.execute("SELECT * FROM inbox WHERE read = :rd AND to_userid = :usr", rd=t, usr=session["user_id"])

    # Return number of unread messages in JSON format
    badge = len(rows)
    return jsonify(badge)
```
There are two ways to send a message to a user :

* *Say Hi to [username]* Button in user's profile page; which works only for logged in users, otherwise it redirects to login page.

![Send message via Say Hi](https://lh3.googleusercontent.com/pw/ACtC-3fJCiYergciFET1EmLzzQLd97En_xdxWSc-tcuXqD9HQGYyAnGFSLl2nbVo6sZs0SI9r2rS-jOh9qIHgZZ04amCim9xatt6mhOr_NNsxE_n-7qjj21fZAoY5rsEVcB1zsBg6k66dkMa6sMAOuEzIy67=w600-h336-no)

* Or *Reply* Button in message's page to reply to a received message

![Send message via Reply](https://lh3.googleusercontent.com/pw/ACtC-3eCEUASat734cwhaZZZX06cC5HSLaWbJdx63bagyiumQrQDEMMKMXRGI76lOvwpilKk3uLuAqHVH21DcreNptbfNO6gP7jGk6kk6HyH-VmfNrZV5ub0h7dIlIV5fTuFudtYKFgeSGYxpaZxGvBMSlkG=w600-h336-no)

In both cases it displays a modal dialog box that contains an input for the message's *Object* and a text area for the message's text. If it is a *Reply*, inbox.html is rendered once the message is sent, if it a *Say Hi* message, the presently displayed user profile is displayed again.
To delete a message, there is *Delete* Button in message's page next to *Reply* button.

![Delete message](https://lh3.googleusercontent.com/pw/ACtC-3fKI-2ugfN1Z4rBowwBFF5XUpzOdD5asHiQemVeB5mfS0HZr6WSvpKJpndy1EE8X5Ttp9D_m26PRDEoSsrKqcuDr-DEB6KTARNJd7ocZ_ermsMAS0QiYvy1mV8M3nGb4IOK6pwpseHGTyyRhvzENEvM=w600-h336-no)

### Get this book

This is somehow the quintessential specificity of this web app, which is the free exchange of Books. In fact, as explained previously, all visible books in Bookex database (hidden books aren't diplayed as shown earlier), can be requested by any user and shall be sent within few days after reception of the *Book request notification* to the address provided there in. Again, as explained above, if the user doesn't want to recieve requests for a specific book of their, they can either delete it from data base or just hide it.

The *Get this book* button is located in every book page right below the Author's name. Once a logged in user clicks it, a modal window pops up to ask for confirmation and to type in the shipping address.
Once user types in their name and address and click confirm, a successfully sent message page template is rendered to inform them that their request was sent to owner.
If the *Get this book* button is clicked again by any user before owner confirms shipment of the book, an information message that the book is already requested and is being sent to his new owner, pops up. That's because the value of *requested* in *Books* table is set to "yes" once the book request is sent.

![Send book request](https://lh3.googleusercontent.com/pw/ACtC-3eMsz1g7OpripauqVE9pHiu3m72V_Efr_YiwzR6DCU-AGr4hkT_Kpp-fVm3Ctt0bhWmh3brL9A4gRb-mgvXnHd_YNsCzS5NV7ulfgc59o0rxdYD3KIdJ39CFSqdYi08KONk3lXLhRgqyZk4bH_eLsaY=w600-h336-no)

Once the book request sent via the *Get this book* button, the ower receives a notification in their inbox containing the informaion about the requested book, the user who sent the request and their full name and address. 

The name of the book and the username in the received notification are clickable links the the user profile page and the book page respectively. When the owner accesses to the book page, a pop up message appears with two inputs appears asking them to fill the shipping information which are Tracking Number and Shipper company name to be transmitted to the new owner, once the book is shipped. 

![Receiving book request](https://lh3.googleusercontent.com/pw/ACtC-3fZjHQOx6JT-6s7q0LAj6m80QTXrU3jO8Z0Mzg9NaLIKg2kaCAgvh7wy4vsRvnHQdmUJhmGPQBB5fw2f0cusmQMek9FNsjuhZ1XRyfwsGpg7QhfYkYGx7UBck0O6qp7k-jFtlglJ_4ashE64c9y2Npl=w600-h336-no)

Once the owner has filled the shipping form and confirms, the shipping information is sent to the new owner's inbox and the book page is immediately updated, with the new owner's name. In fact, *book.html* template is rendered instead of previously displayed *mybook.html*. Furthermore, in data base, the value of *requested* for that book in Books table is set to "no" and the value of *hidden* is set to yes instead. 

![Sending shipping information](https://lh3.googleusercontent.com/pw/ACtC-3e86VDFP-7WoytaoFj2Bn0V3yPednLAZPDlhmIK7gxrAZya7e6HfGQNYOmfzchK_9pyfjK8QzPh8k0mnLyQXR4klwC2XMSCSsR5Z8J5no61j3gSy8I2ynYqHFWqVvtlu7aEhYz_YC1LyNOZZ6SkMC6E=w600-h336-no)

The new owner receives a message, then, informing them about the shipment of the book and giving the shipping information to track the parcel. On bookexChange platform, they're already the owner of the book and so it is added to their own books. 

![New owner receiving shipping information](https://lh3.googleusercontent.com/pw/ACtC-3eNehA4ds-oELZaerIgrogMkLSpLzR0Cpt7AYbwu_eJFc_GRmFZvUMEuQOyg6VPd0OYi2UqC7QW28zaJ2OQa9g5ClcXRdq_jbhM5cGALOWCkDz-Smv8eb1919YsTSxNwKfJyUO2oU1RuVPA_1LTcaVD=w600-h336-no)


However, as the book is automatically turned to *hidden* when the shipping information are sent in order to avoid any book requests during the shipment, they are informed about it in the message as well and can turn the book back to visible by clicking the *Unhide* button.

![Hidden shipped book](https://lh3.googleusercontent.com/pw/ACtC-3fw79BvJ5fKrXA2syimGVfIc6UDXsdRvp5PMzusE3K0uBAHecBoq_iCMjUsoFTJIKAJFhEHd3eUrvt6BrruBegBkSCqjSZHZhnvp5sfcacyxdQa43_9BthwDyq2P-5KW4IHzzhI7UYjXQI61-EDBiQV=w600-h336-no)

#### Regulated gotten books quota

Everytime a book is requested, once it is shipped *gotten* value in *users* table is incremented for the user who requeted the book and *given* value in *users* table is incremented for the user who sent their book. When a user clicks the *get this book* button, if total number of *gotten* books is higher than total number of *given* books, as alert message pops up to inform the user about it. As soon as they ship one book or more, *given* book is incremented and becomes equal to or bigger than *gotten* books which allows the user to send requests to get books again.

![Gotten books quota](https://lh3.googleusercontent.com/pw/ACtC-3eZmhTQoMiM5eJSfe3KwOtgxQ_HpTnA26yvh9HhJlzTT-zSu31ieFTOnWDaOOpzMozvO7x_0lS5DXc7G1dQburvdt2Kkc6DoEPD0v1mcAUGw88cIHuR3ihk06xhws4j_MFJ6loYZp70mzL0TqfoLWfH=w600-h336-no)


## Developed by

Jihen Frikha
