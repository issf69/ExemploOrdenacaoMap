# Uma Vitoria Cada Dia - ExemploOrdenacaoMap
Trabalhando com Collections Java Ordenação - Map
## package aprendendoavidatoda.com.br;

/*Dadas as seguintes informações sobre meus livros favoritos e seus autores,
crie um dicionário e ordene este dicionário:
exibindo (Nome Autor - Nome Livro);
Autor = Paulo Lins - Livro = nome: Cidade de Deus . páginas: 388
Autor = J.K. Rowling- Livro = nome: Harry Potter e a Pedra Filosofal , paginas: 263
Autor = John Grogan   - Livro = nome  Marley e Eu , páginas: 364
*/

import java.util.*;

public class ExemploOrdenacaoMap {
    public static void main(String[] args) {

        System.out.println("--\tOrdem aleatoria\t--");
        Map<String, Livro> meusLivros = new HashMap<>() {{
            put(" Paulo Lins", new Livro("Cidade de Deus", 388));
            put(" J.K. Rowling", new Livro("Harry Potter e a Pedra Filosofal", 263));
            put(" John Grogan", new Livro("Marley e Eu", 364));
        }};
        for (Map.Entry<String, Livro> livro : meusLivros.entrySet())
            System.out.println(livro.getKey() + " - " + livro.getValue().getNome());

        System.out.println("--\tOrdem Insercao\t--");
        Map<String, Livro> meusLivros1 = new LinkedHashMap<>() {{
            put(" Paulo Lins", new Livro("Cidade de Deus", 388));
            put(" J.K. Rowling", new Livro("Harry Potter e a Pedra Filosofal", 263));
            put(" John Grogan", new Livro("Marley e Eu", 364));
        }};
        for (Map.Entry<String, Livro> livro : meusLivros1.entrySet())
            System.out.println(livro.getKey() + " - " + livro.getValue().getNome());

        System.out.println("--\tOrdem alfabetica autores\t--");
        Map<String, Livro> meusLivros2 = new TreeMap<>(meusLivros1);
        for (Map.Entry<String, Livro> livro : meusLivros2.entrySet())
            System.out.println(livro.getKey() + " - " + livro.getValue().getNome());

        System.out.println("--\tOrdem alfabetica nomes dos livros\t--");

        Set<Map.Entry<String, Livro>> meusLivros3 = new TreeSet<>(new ComparatorNome());
        meusLivros3.addAll(meusLivros.entrySet());
        for (Map.Entry<String, Livro> livro : meusLivros3)
            System.out.println(livro.getKey() + " - " + livro.getValue().getNome());

        System.out.println("--\tOrdem numero de pagina\t--");

        Map<String, Livro> numerodePaginas = new TreeMap<>(meusLivros1);
        for (Map.Entry<String, Livro> livro : meusLivros2.entrySet())
            System.out.println(livro.getKey() + " - " + livro.getValue().getPaginas());

        



    }
}

class Livro {
    private String nome;
    private Integer paginas;

    public Livro(String nome, Integer paginas) {
        this.nome = nome;
        this.paginas = paginas;
    }

    public String getNome() {
        return nome;
    }

    public Integer getPaginas() {
        return paginas;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Livro livro = (Livro) o;
        return nome.equals(livro.nome) && paginas.equals(livro.paginas);
    }

    @Override
    public int hashCode() {
        return Objects.hash(nome, paginas);
    }

    @Override
    public String toString() {
        return "Livro{" +
                "nome='" + nome + '\'' +
                ", paginas=" + paginas +
                '}';
    }
}

class ComparatorNome implements Comparator<Map.Entry<String, Livro>>{

    @Override
    public int compare(Map.Entry<String, Livro> l1, Map.Entry<String, Livro> l2) {
        return l1.getValue().getNome().compareToIgnoreCase(l2.getValue().getNome());
    }


}


###  C:\Users\Irene\.jdks\openjdk-18.0.1.1\bin\java.exe "-javaagent:C:\Program Files\JetBrains\IntelliJ IDEA Community Edition 2022.1.1\lib\idea_rt.jar=63989:C:\Program Files\JetBrains\IntelliJ IDEA Community Edition 2022.1.1\bin" -Dfile.encoding=UTF-8 -classpath "C:\Users\Irene\Documents\Collections Java Ordenacao métodos Map - parte 2\Ordenacao-Map\out\production\Ordenacao-Map" aprendendoavidatoda.com.br.ExemploOrdenacaoMap
--	Ordem aleatoria	--
 John Grogan - Marley e Eu
 J.K. Rowling - Harry Potter e a Pedra Filosofal
 Paulo Lins - Cidade de Deus
--	Ordem Insercao	--
 Paulo Lins - Cidade de Deus
 J.K. Rowling - Harry Potter e a Pedra Filosofal
 John Grogan - Marley e Eu
--	Ordem alfabetica autores	--
 J.K. Rowling - Harry Potter e a Pedra Filosofal
 John Grogan - Marley e Eu
 Paulo Lins - Cidade de Deus
--	Ordem alfabetica nomes dos livros	--
 Paulo Lins - Cidade de Deus
 J.K. Rowling - Harry Potter e a Pedra Filosofal
 John Grogan - Marley e Eu
--	Ordem numero de pagina	--
 J.K. Rowling - 263
 John Grogan - 364
 Paulo Lins - 388

Process finished with exit code 0
