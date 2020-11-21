---
C# | File
---

# 1. File

```c#
string text = System.IO.File.ReadAllText("./data.csv");
        System.Console.WriteLine(text);
```

```c#
string[] lines = System.IO.File.ReadAllLines("./data.csv");
foreach (string line in lines) Console.WriteLine(line);
```



        

        



Aby kod z pętli zawsze przynajmniej raz został wykonany (nie zalaeżnie od warunku) trzeba użyć konstrukcji `do..while`:

```c#
do
{
  Console.Write(i + " ");
  i++;
}
while(i < 10) 
```
Nawet gdy i będzie większe od 10 to jego wartość wyświetli się na konsoli chociaż raz.

W przypadku iteracji pętle **while** możemy zastąpić pętlą **for**. Wówczas składnia takiej operacji się nieco upraszcza.

```c#
one-tine-executed;
while(condition)
{
  // [...]
  every-time-executed;
}

for(one-tine-executed; condition; every-time-executed) 
{
  // [...]
}
```

```c#
int i = 0;
while(i < 10)
{
  Console.Write(i + " ");
  i++;
}

for(int i = 0; i < 10; i++) 
{
  Console.Write(i + " ");
}
```
Gdy chcemy zakończyć działanie pętli w sytuacji, której nie przewiduje warunek możemy tego dokonać za pomocą instrukcji `break`

```c#
for(int i = 0; i < 10; i++) 
{
  if(i == 3) break;
  Console.Write(i + " ");
}
```
Wówczas zostanie wyświetlone

    0 1 2

Aby pominąć iteracje dla pojedynczego przypadku, bez wyjści z pętli można użyć instukcji `continue`.

```c#
for(int i = 0; i < 10; i++) 
{
  if(i == 3) continue;
  Console.Write(i + " ");
}
```
Wówczas zostanie wyświetlone

    0 1 2 4 5 6 7 8 9

Jeżeli chcemy przełamać `n`-tą ilość pętli lub pominąć `n`-tą ilość iteracji wystarczy do powyższych instrukcji dodać liczbę.

```c#
break n;
continue n;
```

Mając tą wiedze napisanie programu, który pobierze od użytkownika liczby `start` i `end` typu `int` oraz wyświetli kolejne liczby zaczynając do `start`, a kończąc na `end`.

Jak użyłem do tego zadania pętli `for` zmień go tak, aby wykorzystać pętle `while`. Gdy użyłeś `while` przkształć go tak, aby teraz użyć `for`. 

<!---
--->

## Zadanie

Napisać program, który wylicza wypisuje liczby pierwsze od 2 do podanej przez użytkownika liczby

Rozwiązanie:

```c#
Console.Write("Length: ");
int n = int.Parse(Console.ReadLine());
  
double[] arr = new double[n];

for(int i = 0; i < n; i++)
{
  Console.Write("Element[" + i + "]: ");
  arr[i] = double.Parse(Console.ReadLine());
}

// TODO: 

Console.Write("Output:");
for(int i = 0; i < n; i++)
{
  Console.Write(" " + arr[i]);
}
```

# 2. Tablice

Tablice możemy zadeklarować na 2 sposoby.
Deklarując pustą tablicę o długości `n`.

```c#
double[] nbr = new double[n];
```
Wprowadzając do tablicy konkretne wartości

```c#
double[] nbr = { 12, 45, 56.5, 8, 94 };
```
Wypisanie wszystkich elementów tablicy można zrealizować oczywiście za pomocą pętli `for` 

```c#
for(int i = 0; i < nbr.Length; i++)
  Console.WriteLine("nbr[" + i + "] = " + nbr[i]);         
```
    nbr[0] = 12    
    nbr[1] = 45
    nbr[2] = 56,5
    nbr[3] = 8
    nbr[4] = 94

Jednak, gdy nie jest potrzebny nam index tablicy, to bardziej elegancko użyć jest pętli `foreach`.

```c#
foreach(double nbr_i in nbr)
    Console.Write(nbr_i + " "); 
```
    12 45 56,5 8 94

W tej pętli deklarowana jest zmienna pomocnicza. W naszym przypadku `nbr_i` i podczas kolejnych iteracji umieszczane w nim są kolejne elementy z tablicy.

Jak już torszkę ogarniamy pętle i tablicę możnaby napisac program, który pobiera od urzytkownika długośc tablicy, a następnie wszystkie jej elementy. Dodatko jak 


, na samym końcu je wypisuje. 



Pierzym krokiem będzie pobranie operacji arytmentycznej podanej przez użytkownika (`+`, `-`, `*`, `/`) oraz liczby z kają ta operacja ma być wykonana.

Opracj ma być wykonana na wszystkich elementach tablicy podanej przez użytkownika. Przykładowo dla dodawania:

```c#
for(int i = 0; i < n; i++) arr[i] += y
```

Gdzie `y` jest liczbą podaną przez użytkownika. Kolejnym krokiem będzie zmiana sposobu wprowadzania liczb przez użytkownika. Użytkownik poda łańcuch liczb oddzielonych spacjami. Przykładowo.

    12 45 56.5 8 94

Naszym zadaniem będzie przkształcenie tego łańcucha znaków na tablicę typu double.

```c#
{ 12 45 56.5 8 94 }
```
Do realizaji tego zadania pomocna może okazać się metoda `Split1

```c#
string str = Console.ReadLine();
String[] list = str.Split(" ");
```

```c#
double[] table = Array.ConvertAll(str.Split(mychars), new Converter<string, double>(double.Parse));
```

<!---
```c#
foreach(string element in list) Console.Write(element + " ");
```
--->

## Zadanie 2
Program wypisujący liczby peirwsze - poprzednie zadanie:

```c#
Console.Write("End: ");

int end = int.Parse(Console.ReadLine());
bool flag;

for(int i = 1; i <= end; i++)
{
  c = true;
  for (int j = 2; j <= Math.Sqrt(i); j++)
  {
    if(i % j == 0)
    {
      flag = false;
      break;
    }
  }
  if(flag == true) Console.Write(i + " ");
}
```
Program taki jest dość wolny podczas szukania bardzo dużych liczb pierwszych. Dlatego, żeby go przyspieszyć będziemy zapisywać znalezione liczby pierwsze i sprawdzać dzielenie tylko przez liczby z tablicy. Ponieważ gdy liczba nie dzieli się przez wszystkie mniejsze od niej liczy pierwsze to tym bardziej nie dzieli się przez ich wielokrotności. Do dzieła!