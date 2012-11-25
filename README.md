# JSONSerializer
By Alexander Forselius <drsounds@gmail.com> for org.json package.

An extension to the org.json package, which adds a simple class that allows you to serialize simple objects from any class into JSONOBject.

# Example usage

Consider this class

    public class Author {
        private String firstname;
        /**
         * @return the firstname
         */
        public String getFirstname() {
            return firstname;
        }
        /**
         * @param firstname the firstname to set
         */
        public void setFirstname(String firstname) {
            this.firstname = firstname;
        }
        /**
         * @return the lastname
         */
        public String getLastname() {
            return lastname;
        }
        /**
         * @param lastname the lastname to set
         */
        public void setLastname(String lastname) {
            this.lastname = lastname;
        }
        private String lastname;
    }
    public class Book {
        private String title = "";
        /**
         * @return the title
         */
        public String getTitle() {
            return title;
        }
        /**
         * @param title the title to set
         */
        public void setTitle(String title) {
            this.title = title;
        }
        private Author[] author;
        /**
         * @return the author
         */
        public Author[] getAuthor() {
            return author;
        }
        /**
         * @param author the author to set
         */
        public void setAuthor(Author[] author) {
            this.author = author;
        }
    }

To serialize an instance into a JSON object, we can do this

    JSONSerializer serializer = new JSONSerializer();
    Book book = new Book();
    book.title = "Test";
    book.author = new Author[]{new Author(), new Author()};
    book.author[0].firstname = "Alecca";
    book.author[0].lastname = "Krikelin";
    book.author[1].firstname = "Alexander";
    book.author[1].lastname = "Forselius";
    JSONObject jsonBook = serializer.deserialize(book);	
    System.out.println(jsonBook)

Inspecting it will return:	

    {"author":[{"lastname":"Krikelin","firstname":"Alecca"},{"lastname":"Forselius","firstname":"Alexander"}],"title":"Test"}
	

