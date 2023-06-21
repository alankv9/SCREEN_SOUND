// Screen Sound
string mensagemDeBoasVinda = "\nBoas vindas ao Screen Sound";
//List<string> ListaDasBandas = new List<string> {"Matuê", "Teto","Kalli"};
Dictionary<string, List<int>> bandasRegistradas = new Dictionary<string, List<int>>();
bandasRegistradas.Add("Linkin Park", new List<int> {10, 9, 8});
bandasRegistradas.Add("Teto", new List<int> ());
bandasRegistradas.Add("Matuê", new List<int> { 10, 8, 9 });
void ExibirLogo()
{
    Console.WriteLine(@"
░██████╗░█████╗░██████╗░███████╗███████╗███╗░░██╗  ░██████╗░█████╗░██╗░░░██╗███╗░░██╗██████╗░
██╔════╝██╔══██╗██╔══██╗██╔════╝██╔════╝████╗░██║  ██╔════╝██╔══██╗██║░░░██║████╗░██║██╔══██╗
╚█████╗░██║░░╚═╝██████╔╝█████╗░░█████╗░░██╔██╗██║  ╚█████╗░██║░░██║██║░░░██║██╔██╗██║██║░░██║
░╚═══██╗██║░░██╗██╔══██╗██╔══╝░░██╔══╝░░██║╚████║  ░╚═══██╗██║░░██║██║░░░██║██║╚████║██║░░██║
██████╔╝╚█████╔╝██║░░██║███████╗███████╗██║░╚███║  ██████╔╝╚█████╔╝╚██████╔╝██║░╚███║██████╔╝
╚═════╝░░╚════╝░╚═╝░░╚═╝╚══════╝╚══════╝╚═╝░░╚══╝  ╚═════╝░░╚════╝░░╚═════╝░╚═╝░░╚══╝╚═════╝░");
    Console.WriteLine(mensagemDeBoasVinda);
}

void ExibirOpcoesDoMenu()
{
    ExibirLogo();
    Console.WriteLine("\nDigite 1 para resgistra uma banda");
    Console.WriteLine("Digite 2 para mostra todas as bandas");
    Console.WriteLine("Digite 3 para avaliar uma banda");
    Console.WriteLine("Digite 4 para exibir a média de uma banda");
    Console.WriteLine("Digite -1 para sair");

    Console.Write("\nDigite a sus opção:");
    string opçaoEscolhida =Console.ReadLine()!;
    int opcaoEscolhidaNumerica = int.Parse(opçaoEscolhida);

    switch (opcaoEscolhidaNumerica)
    {
        case 1: RegistraBanda();
            break;
        case 2: ExibirBandasRegistradas();
            break;
        case 3: AvaliarUmaBanda();
            break;
        case 4:ExibirMediaBanda();
            break;
        case -1:Console.WriteLine("Tchau tchau :)");
            break;
        default: Console.WriteLine("Opçao inválida");
            break;
    }


}
void RegistraBanda()
{
    Console.Clear();
    ExibirTituloDaOpçao("Registro das bandas");
    Console.Write("Digite o nome da banda que deseja resgistrar:");
    string nomeDaBanda = Console.ReadLine()!;
    bandasRegistradas.Add(nomeDaBanda, new List<int>());
    Console.WriteLine($"A banda {nomeDaBanda} foi registrada com sucesso");
    Thread.Sleep(2000);
    Console.Clear();
    ExibirOpcoesDoMenu();
}

void ExibirBandasRegistradas()
{
    Console.Clear() ;
    ExibirTituloDaOpçao("Exinbindo todas as bandas registradas");
    //for (int i = 0; i < ListaDasBandas.Count; i++)
   // {
       // Console.WriteLine($"Banda: {ListaDasBandas[i]}");
   // }]
    foreach (string banda in bandasRegistradas.Keys)
    {
        Console.WriteLine($"Bandas: {banda}");
    }
    Console.WriteLine("\nDigite uma tecla para volta ao menu principal");
    Console.ReadKey();
    Console.Clear();
    ExibirOpcoesDoMenu();
}

void ExibirTituloDaOpçao(string titulo)
{
    int quantidadeDeLetras = titulo.Length;
    string asteriscos = string.Empty.PadLeft(quantidadeDeLetras, '*');
    Console.WriteLine(asteriscos);
    Console.WriteLine(titulo);
    Console.WriteLine(asteriscos + '\n');
}

void AvaliarUmaBanda ()
{
    //digite qual banda deseja avaliar
    //se a banda exitir no dicionario >> atribuir uma nota
    // senão, volta ao menu principal

    Console.Clear();
    ExibirTituloDaOpçao("Avaliar banda");
    Console.WriteLine("Digite o nome da banda que deseja avaliar:");
    string nomeDaBanda = Console.ReadLine()!;
    if (bandasRegistradas.ContainsKey(nomeDaBanda))
    {
        Console.Write($"Qual a nota que a bandas {nomeDaBanda} merece:");
        int nota = int.Parse(Console.ReadLine()!);
        bandasRegistradas[nomeDaBanda].Add(nota);
        Console.WriteLine($"\nA nota {nota} foi registrada com sucesso para a banda {nomeDaBanda}");
        Thread.Sleep(4000);
        Console.Clear();
        ExibirOpcoesDoMenu();
    }
    else
    {
        Console.WriteLine($"\nA banda {nomeDaBanda} não foi encontrada");
        Console.WriteLine("Digite uma tecla para volta ao menu principal");
        Console.ReadKey();
        Console.Clear();
        ExibirOpcoesDoMenu();

    }
}

void ExibirMediaBanda ()
{
    Console.Clear();
    ExibirTituloDaOpçao("Exibir média da banda");
    Console.Write("Digite o neme da banda que deseja exibir a média:");
    string nomeDaBanda = Console.ReadLine();
    if (bandasRegistradas.ContainsKey(nomeDaBanda))
    {
        List<int> notasDasBanda = bandasRegistradas[nomeDaBanda];
        Console.WriteLine($"\nA média da banda {nomeDaBanda} é {notasDasBanda.Average()}.");
        Console.WriteLine("Digite uma tecla para volta ao menu principal");
        Console.ReadKey();
        Console.Clear();
        ExibirOpcoesDoMenu();

    }
    else
    {
        Console.WriteLine($"\nA banda {nomeDaBanda} não foi encontrada");
        Console.WriteLine("Digote uma tecla para volta ao menu");
        Console.ReadKey();
        Console.Clear();
        ExibirOpcoesDoMenu();
    }


}
ExibirOpcoesDoMenu();
