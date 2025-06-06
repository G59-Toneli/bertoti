# ENGENHARIA DE SOFTWARE 1
## Programming Over Time
## Texto 1
We propose that “software engineering” encompasses not just the act of writing code, but all of the tools and processes an organization uses to build and maintain that code over time.
What practices can a software organization introduce that will best keep its code valuable over the long term? How can engineers make a codebase more sustainable and the software engineering discipline itself more rigorous? We don’t have fundamental answers to these questions, but we hope that Google’s collective experience over the past two decades illuminates possible paths toward finding those answers. 
One key insight we share in this book is that software engineering can be thought of as “programming integrated over time.” 
What practices can we introduce to our code to make it sustainable—able to react to necessary change—over its life cycle, from conception to introduction to maintenance to deprecation?
The book emphasizes three fundamental principles that we feel software organizations should keep in mind when designing, architecting, and writing their code:
 
### Time and Change
How code will need to adapt over the length of its life
 
### Scale and Growth
How an organization will need to adapt as it evolves
 
### Trade-offs and Costs
How an organization makes decisions, based on the lessons of Time and Change and Scale and Growth

>> Engenharia de software aborda tudo aquilo que envolve o ambiente de programação, não somente o ato de escrever o codigo mas tambem sua longevidade e manutenção conforme novas tecnologias surgem.

## Texto 2

What precisely do we mean by software engineering? What distinguishes “software engineering” from “programming” or “computer science”? And why would Google have a unique perspective to add to the corpus of previous software engineering literature written over the past 50 years?
 
The terms “programming” and “software engineering” have been used interchangeably for quite some time in our industry, although each term has a different emphasis and different implications. University students tend to study computer science and get jobs writing code as “programmers.”
 
“Software engineering,” however, sounds more serious, as if it implies the application of some theoretical knowledge to build something real and precise. Mechanical engineers, civil engineers, aeronautical engineers, and those in other engineering disciplines all practice engineering. They all work in the real world and use the application of their theoretical knowledge to create something real. Software engineers also create “something real,” though it is less tangible than the things other engineers create.
 
Unlike those more established engineering professions, current software engineering theory or practice is not nearly as rigorous. Aeronautical engineers must follow rigid guidelines and practices, because errors in their calculations can cause real damage; programming, on the whole, has traditionally not followed such rigorous practices. But, as software becomes more integrated into our lives, we must adopt and rely on more rigorous engineering methods. We hope this book helps others see a path toward more reliable software practices.

>> A principal diferenciação de um progamador para um engenheiro de software, seria a criação de algo "real" pelo engenheiro, algo que não se limita somente ao mundo dos códigos mas sim que interage diretamente com as pessoas.

</p>

# Exemplos de Tradeoff

### Exemplo 1:
<p> Ao usar a linguagem de programação python, se ganha facilidade e simplicidade na programação, em troca de poder de processamento.</p>

### Exemplo 2:

<p> Ao fazer uso da linguagem C, é utilizado de um poder maior de processamento, em troca de uma linguagem mais complexa, por ser mais próxima da máquina.</p>

### Exemplo 3:

<p> O SO Linux é gratuito, mais seguro e leve do que o Windows, porém, possui uma compatilibilidade com softwares e hardwares e uma interface menos intuitiva.</p>

# Comentario sobre o slide 57:
<p>
 É apresentado o conceito de que mais vale uma grande ideia apresentada do que um pequeno produto que ainda esta sendo desenvolvido
</p>

# Codigo Java: 

 ### 1. Book.java


package library;

public class Book {
    private String title;
    private String author;
    private String publisher;
    private String isbn;
    private int year;
    private int pages;

    public Book(String title, String author, String publisher, String isbn, int year, int pages) {
        this.title = title;
        this.author = author;
        this.publisher = publisher;
        this.isbn = isbn;
        this.year = year;
        this.pages = pages;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public String getPublisher() {
        return publisher;
    }

    public void setPublisher(String publisher) {
        this.publisher = publisher;
    }

    public String getIsbn() {
        return isbn;
    }

    public void setIsbn(String isbn) {
        this.isbn = isbn;
    }

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public int getPages() {
        return pages;
    }

    public void setPages(int pages) {
        this.pages = pages;
    }
}

### 2. Library.java

package library;

import java.util.LinkedList;
import java.util.List;

public class Library {
    private List<Book> books = new LinkedList<>();

    public void addBook(Book book) {
        books.add(book);
    }

    public Book searchByIsbn(String isbn) {
        for (Book book : books) {
            if (book.getIsbn().equals(isbn)) return book;
        }
        return null;
    }

    public List<Book> searchByAuthor(String author) {
        List<Book> result = new LinkedList<>();
        for (Book book : books) {
            if (book.getAuthor().equalsIgnoreCase(author)) result.add(book);
        }
        return result;
    }

    public List<Book> getBooks() {
        return books;
    }
}

### 3. Test.java


package library;

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

class TestLibrary {

    @Test
    void testLibraryOperations() {
        Library library = new Library();

        library.addBook(new Book("1984", "George Orwell", "Companhia das Letras", "978-8535914849", 1949, 328));
        library.addBook(new Book("A Revolução dos Bichos", "George Orwell", "Companhia das Letras", "978-8535913941", 1945, 152));
        library.addBook(new Book("Dom Casmurro", "Machado de Assis", "Editora Ática", "978-8508152710", 1899, 256));

        assertEquals(3, library.getBooks().size());

        Book book = library.searchByIsbn("978-8535914849");
        assertEquals("1984", book.getTitle());

        List<Book> orwellBooks = library.searchByAuthor("George Orwell");
        assertEquals(2, orwellBooks.size());
    }
}



