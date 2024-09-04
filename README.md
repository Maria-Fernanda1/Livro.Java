package Livro;

public class Livro {
    private String titulo;
    private String autor;
    private int numCopias;
    private int livrosReservados;

    public Livro(String titulo, String autor, int numCopias) {
        this.titulo = titulo;
        this.autor = autor;
        this.numCopias = numCopias;
        this.livrosReservados = 0;
    }

    public String getTitulo() {
        return titulo;
    }

    public String getAutor() {
        return autor;
    }

    public int getNumCopias() {
        return numCopias;
    }

    public int getLivrosReservados() {
        return livrosReservados;
    }

    public void reservarLivro() throws LivroIndisponivelException {
        if (numCopias - livrosReservados <= 0) {
            throw new LivroIndisponivelException("Não há cópias disponíveis para o livro: " + titulo);
        }
        livrosReservados++;
    }

    public void devolverLivro() {
        if (livrosReservados > 0) {
            livrosReservados--;
        }
    }

    public boolean isDisponivel() {
        return numCopias - livrosReservados > 0;
    }

    @Override
    public String toString() {
        return "Título: " + titulo + ", Autor: " + autor + ", Cópias Disponíveis: " + (numCopias - livrosReservados);
    }
}

