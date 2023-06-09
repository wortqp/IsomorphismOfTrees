![isomorphic trees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/FEFU_logo.jpg)
## Федеральное агентство по образованию РФ
## Дальневосточный федеральный университет
## ИНСТИТУТ МАТЕМАТИКИ И КОМПЬЮТЕРНЫХ ТЕХНОЛОГИЙ
## Департамент математического и компьютерного моделирования
# Изоморфизм деревьев
## Отчет
### Студента гр. Б9121-09.03.03пикд
### Карповой Ю. С.
### Руководитель
### Кленин А. С.
### г. Владивосток 2023


--------------------------
# 1. Введение
## 1.1 Глоссарий
- `Матрица смежности` - это квадратная матрица, в которой каждый элемент принимает одно из двух значений: `0` или `1`, где 1 - наличие ребра (связи) между узлами, а 0 - отсутствие. 
- `Подвешенное дерево` - это ориентированный граф без циклов, в котором в каждую вершину, кроме одной, называемой корнем ориентированного дерева, входит одно ребро.
- `Некорневое дерево` - это ориентированный граф без циклов, который не содержит корня и отражает связь листьев без предполагаемого положения общего предка.

## 1.2 Формальная постановка задачи
1. Изучить алгоритм "Изоморфизм деревьев" и описать его в форме научного доклада.
2. Реализовать алгоритм определения изоморфности деревьев.
4. Результат работы выложить на github.

## 1.3 Вступление
**Изоморфизм** - логико-математическое понятие, выражающее одинаковость строения (структуры) систем (процессов, конструкций).
**Дерево** — одна из наиболее широко распространённых структур данных в информатике, эмулирующая древовидную структуру в виде набора связанных узлов. Является связным графом, не содержащим циклы. Большинство источников также добавляет условие на то, что рёбра графа не должны быть ориентированными. В дополнение к этим трём ограничениям, в некоторых источниках указывается, что рёбра графа не должны быть взвешенными.
Деревья считаются **изоморфными** в том случае, если они имеют одинаковую структуру, но различный внешний вид.
| ![isomorphic trees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/trees.png) |
| :--: |
| Рис. 1: Изоморфные деревья |

## 1.4 История
### 1.4.1 Первое использование и «открытие» теории графов
Швейцарский, прусский и российский математик Леонард Эйлер в статье (на латинском языке, изданной Петербургской академией наук) о решении знаменитой задачи о кёнигсбергских мостах, датированной 1736 годом, первым применил идеи теории графов при доказательстве некоторых утверждений. При этом Эйлер не использовал ни сам термин «граф», ни какие-либо термины теории графов, ни изображения графов. Леонард Эйлер считается отцом теории графов (как и топологии), открывшим понятие графа, а 1736 год назначен годом рождения теории графов.
### 1.4.2 Второе «открытие» графов
В 1847 году немецкий физик Густав Кирхгоф фактически разработал теорию деревьев при решении системы уравнений для нахождения величины силы тока в каждом контуре электрической цепи. Кирхгоф фактически изучал вместо электрической цепи соответствующий ей граф и показал, что для решения системы уравнений нет необходимости анализировать каждый цикл графа, достаточно рассмотреть только независимые циклы, определяемые любым остовным деревом графа.
### 1.4.3 Третье «открытие» графов
В 1857 году английский математик Артур Кэли, занимаясь практическими задачами органической химии, открыл важный класс графов — деревья. Кэли пытался перечислить химические изомеры предельных (насыщенных) углеводородов CnH2n+2 с фиксированным числом n атомов углерода.
### 1.4.4 Четвертое «открытие» графов
В 1859 году ирландский математик сэр Уильям Гамильтон придумал игру «Вокруг света». В этой игре использовался додекаэдр, каждая из 20 вершин которого соответствовала известному городу. От играющего требовалось обойти «вокруг света», то есть пройти по рёбрам додекаэдра так, чтобы пройти через каждую вершину ровно один раз.
### 1.4.5 Пятое «открытие» графов
В 1869 году, независимо от Артура Кэли, французский математик Камиль Жордан (в частности, в статье « Sur les assemblages de lignes ») придумал и исследовал деревья в рамках чистой математики. При этом Жордан использовал термины теории графов «вершина» (фр. sommet) и «ребро» (фр. arête), но вместо термина «граф» было «соединение рёбер» (фр. assemblage d’arêtes) или просто «соединение» (фр. assemblage). Рисунки Жордан не использовал. При этом Жордан не подозревал о значении своего открытия для органической химии.
### 1.4.6 Начало систематического использования слова «граф» и диаграмм графов
В начале XX века венгерский математик Денеш Кёниг первый предложил называть эти схемы «графами» и изучать их общие свойства. В 1936 году вышла первая в мире книга по теории графов (на немецком языке) Денеша Кёнига «Теория конечных и бесконечных графов» с большей частью результатов за прошедшие 200 лет, начиная с 1736 года — даты выхода первой статьи Леонарда Эйлера по теории графов с решением задачи о кёнигсбергских мостах. В частности, в книге Кёнига имеется общий параграф для задачи о кёнигсбергских мостах и задаче о домино (построение замкнутой цепи из всех костей домино по правилам игры).
## 1.5 Использование
Алгоритм определения **изоморфности деревьев** используется в основном как база для написания других алгоритмов, основанных на структуре дерева.
Одним из таких алгоритмов является алгоритм для **определения симметричности деревьев**.
## 1.6 Математическая модель и ограничения
Пусть дерево задается матрицей смежности. Два дерева с матрицами смежности $c_1$ и $c_2$ называются изоморфными, если существует такая перестановка $p$, что ∀i, j : $c_1[pi, pj] = c_2[i, j]$. Изоморфизм корневых деревьев определяется аналогично. Разница в том, что корень переходит в корень $(p_{root_1} = root_2)$.

Алгоритм работает за `O(n log n)`, при этому все, кроме сортировки работает за `O(n)`. Важно обратить внимание на выбор хеш функции. Пример: пусть есть дерево (1, 2), (1, 3), (1, 4) и дерево (1, 2), (1, 3), (3, 4), (3, 5). Хеш от вектора определяется функцией: 
$$31^n+\sum_{i=1}^{n} 31^{n-i}*a_i$$
`Деревья различны` и их `хэш функции различны`, из чего можно сделать вывод о том, что деревья не изоморфны.
Ограничения:
- Алгоритм определения изоморфности деревьев **требует корректности входных данных**. 
- Количество узлов дерева не может превышать $2^{32}$

-----------------------------
# 2. Поддерживаемые операции
- `isomorphic(otherTree)` — определение изоморфности текущего дерева с другим `(otherTree)`.

| isomorphic |
| ------- |
| $$O(nlog(n))$$ |
-----------------------------
# 3. Реализация
[Исходный код](https://github.com/wortqp/IsomorphismOfTrees).
## 3.1 Структура
### 3.1.1 Поля дерева (Tree)
- `nodes` - список (вектор) всех узлов в дереве.
- `numbers` - ассоциативный массив (Map) хешей сортированных списков (List) и их номеров.
```java
    private List<Node> nodes = new ArrayList<>();
    private Map<List<Integer>, Integer> numbers;
```
| ![fieldTree](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/fieldTree.png) |
| :--: |
| Рис. 2: Представление дерева в алгоритме. |

#### 3.1.2 Поля узла (Node)
- `subNodes` - список узлов, с которыми есть связь (ребра).

```java
    private List<Node> subNodes = new ArrayList<>();
```
| ![fieldSubNodes](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/fieldSubNodes.png) |
| :--: |
| Рис. 3: Связанные узлы узла 1. |

### 3.1.3 Конструктор
Конструктор считывает данные из файла в определенном формате и на их основе строит дерево.
Пример файла для дерева на Рис.2:

```
1: 2 5 8
2: 1 3 4
3: 2
4: 2
5: 1 6 7
6: 5
7: 5
8: 1
```
```java
public Tree(File file) {
        try (BufferedReader in = new BufferedReader(new FileReader(file))) {

            String str;
            while ((str = in.readLine()) != null) {

                Matcher matcher = Pattern.compile("\\d+").matcher(str);
                if (matcher.find()) {
                    int node = Integer.parseInt(matcher.group());
                    add(node);
                    while (matcher.find()) {
                        int subNode = Integer.parseInt(matcher.group());
                        add(subNode);
                        List<Node> subNodes = get(node).subNodes;
                        subNodes.add(get(subNode));
                    }
                }

            }

            for (int i = 0; i < nodes.size(); i++)
                if (nodes.get(i) == null) {
                    nodes.remove(i);
                    i--;
                }
            try {
                isomorphic(this);
            } catch (StackOverflowError e) {
                nodes.clear();
                System.err.println("Invalid data tree have loop. File: " + file);
            }

        } catch (FileNotFoundException e) {
            System.err.println(e.getMessage());
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
}
```
### 3.1.4 Вспомогательные функции
- `add(index)` - добавляет по индексу узел в список всех узлов в дереве.
- `get(index)` - берет узел по индексу из списка всех узлов в дереве.
- `toString()` - возвращает представление дерева в виде стоки.
- `Node.toString()` - возвращает представление узла в виде стоки.
- `ArrayList.hashCode()` - вычисляет хеш код для списка (вектора).


```java
private void add(int index) {
    index--;
    for (;;)
        try {
            if (nodes.get(index) == null)
                nodes.set(index, new Node());
            return;
        } catch (IndexOutOfBoundsException e) {
            nodes.add(null);
        }
}
```
```java
private Node get(int index) {
    index--;
    return nodes.get(index);
}
```
```java
@Override
public String toString() {
    StringBuilder sb = new StringBuilder("Tree {\n");
    for (Node node: nodes) {
        sb.append("    ");
        sb.append(node);
        sb.append(" -> ");
        sb.append(node.subNodes);
        sb.append("\n");
    }
    sb.append("}");
    return sb.toString();
}
```
**Node**
```java
@Override
public String toString() {
    return "@" + hashCode();
}
```
**ArrayList**
```java
int hashCode() {
   final Object[] es = elementData;
   int hashCode = 1;
   for (int i = from; i < to; i++) {
       Object e = es[i];
       hashCode = 31 * hashCode + (e == null ? 0 : e.hashCode());
   }
   return hashCode;
}
```
## 3.2 Алгоритм
### 3.2.1 Описание
Даны `два некорневых дерева`. Проверяем, изоморфны ли они. 
- Возьмем случайно выбранный узел из первого дерева за корень и определим его хеш рекурсивно, как хеш сортированного списка (вектора) хешей детей. 
- Деревья изоморфны, если хеши корней совпадают, поэтому проходимся по узлам второго дерева, определяя их хеши, и если хоть один совпадает с хешем корня первого дерева, то деревья изоморфны. 
- При этом хеш функция должна обладать следующим свойством: хеши различных списков (векторов) различны.

Рассмотрим на примере деревьев на Рис.4.
| ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrameTrees.png) |
| :--: |
| Рис. 4: Рассматриваемые деревья. |
- Случайно выберем узел, например `4`.

| ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame2.png) |
| :--: |
| Рис. 5: Рассматриваемые деревья. |
- Рекурсивно переберем потомков и узнаем номера их хешей
    - когда встетится первый потомок, у которого нет других потомков (лист `1`) записываем хеш пустого списка потомков под номером 1.
    
    | ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame3.png) |
    | :--: |
    | Рис. 6: Рассматриваемые деревья. |
    - возвращаемся к предку листа `1` (узел `2`) и продолжаем перебирать его потомков.
    - переходим к листу `3`, хеш которого соотносится с номером 1, т.к хеш от листа уже записан.
    
    | ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame4.png) |
    | :--: |
    | Рис. 7: Рассматриваемые деревья. |
    - возвращаемся к узлу `2`, список хешей потомков - [1,1], а это в свою очередь новый вид списка, соотнесем его хеш с номером 2.
    
    | ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame5.png) |
    | :--: |
    | Рис. 8: Рассматриваемые деревья. |
    - доходим до листа `6`, соотносим с номером 1.
    
    | ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame6.png) |
    | :--: |
    | Рис. 9: Рассматриваемые деревья. |
    - возвращаемся к узлу `5`, его список - [1], т.к такого варианта еще нет, то соотносим его с новым номером - 3.
    
    | ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame7.png) |
    | :--: |
    | Рис. 10: Рассматриваемые деревья. |
- Дойдя до места, с которого мы начали, список хешей потомков - [2,3], соотносим его с новым номером - **4** - это и есть номер хеша случайно выбранного корня.

| ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame8.png) |
| :--: |
| Рис. 11: Рассматриваемые деревья. |

- Аналогично перебераем каждый узел второго дерева (представляя их корнями) и сравниваем номер хеша их потомков с номером хеша узла `4` из первого дерева, пока не будет совпадения. Если хотя бы один совпадает, то деревья изоморфны.
    - у узла `4` номер хеша 6, следовательно он не подходит.
    
    | ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame9.png) |
    | :--: |
    | Рис. 12: Рассматриваемые деревья. |
    - выберем узел `3`, его список [2,3], следовательно его хеш под номером **4**, такой же как у выбранного узла из первого дерева, следовательно они изоморфны.
    
    | ![exampleTrees](https://github.com/wortqp/IsomorphismOfTrees/blob/master/images/exFrame10.png) |
    | :--: |
    | Рис. 13: Рассматриваемые деревья. |
    
### 3.2.2 isomorphic(other)
1.`isomorphic(other)`- определяет изоморны ли деревья.
    - `other: Tree` - параметр, другое дерево, которое сравниваем с текущим.
    - `boolean` - тип возвращаемого значения.
    
2.`Node.isomorphic(parent)` - вспомогательный метод для `isomorphic(other)`, который рекурсивно проходит по всем узлам дерева и возвращает номер хеша списка (вектора) хешей детей.
    - `parent: Node` - параметр, условный родитель текущего узла.
    - `int` - тип возвращаемого значения, номер хеша из `numbers: Map`.

1. После вызова этого метода на экземпляре дерева:

    1.1 Проверяем, не пусты ли оба дерева, если пусты, то возвращаем `true` - *деревья изоморфны*.
    
    1.2 Проверяем, равны ли размеры деревьев (количество узлов), если нет, то возвращаем `false` - *деревья не изоморфны*.
    
    1.3 Создаем новый `Map` для `numbers`.
    
    1.4 Выбираем случайный узел текущего дерева за корень.
    
    1.5 Узнаем номер хеша корня вызовом метода `Node.isomorphic(null)`.
  
  
   2. После вызова этого метода у выбранного корня:
    
      2.1 Создаем новый список номеров хешей `nums`.
        
      2.2 Рекурсивно вызываем у всех узлов, с которыми есть связь, кроме узла `parent`, метод `Node.isomorphic(this)` и добавляем их номера хешей в `nums`.
        
      2.3 Сортироуем `nums` по возрастанию.
        
      2.4 Проверяем, содержится ли такой список (вектор) `nums` в `Map` `numbers`, если такого списка нет, то добавляем его и соотносим с номером, который равен текущему размеру `Map` `numbers` + 1.
        
      2.5 Возвращаем номер `nums` из `numbers`.
       
       
    1.6 Присваеваем получившийся `Map` `numbers` сравниваему дереву (чтобы была общая мапа на два дерева).
    
    1.7 Перебираем все узлы у сравниваемого дерева, принимая каждый за корень, вызываем метод `Node.isomorphic(null)` и сравниваем возвращенный номер хеша с хешом с выбранным корнем их первого дерева *(1.5)*, если хоть один совпадает, то возвращаем `true` - *деревья изоморфны*.
    
    1.8 Если ни один не совпадает, то возвращаем `false` - деревья не изоморфны.  

```java
public boolean isomorphic(Tree other) {
    if (nodes.isEmpty() && other.nodes.isEmpty())
        return true;
    if (nodes.size() != other.nodes.size())
        return false;

    numbers = new HashMap<>();
    Node root = nodes.get(new Random().nextInt(nodes.size()));
    int number = root.isomorphic(null);
    other.numbers = numbers;
    for (Node node: other.nodes) {
        if (number == node.isomorphic(null)) {
            return true;
        }
    }
    return false;
}
```
**Node**
```java
private int isomorphic(Node parent) {
    List<Integer> nums = new ArrayList<>();
    for (Node node: subNodes) {
        if (node != parent)
            nums.add(node.isomorphic(this));
    }

    Collections.sort(nums);
    if (!numbers.containsKey(nums))
        numbers.put(nums, numbers.size()+1);
    return numbers.get(nums);
}
```
-----------------------------
# 4. Тестирование
## 4.1 Входные данные
Текстовый файл, в каждой строке которого:
- данные вида `число:` - индексы узлов.
- данные вида число: `число*1* число*2* ... число*n*` - индексы узлов, на которые он ссылается.

**Примеры**
```
Sample1_6nodes_structure1
```
- SampleX - номер примера.
- Xnodes - кол-во узлов.
- structureX - структура дерева. 

*Sample1_6nodes_structure1*
```
1: 2 3
2: 1 4 5
3: 1
4: 2 6
5: 2
6: 4
```

*Sample2_6nodes_structure1*
```
1: 2 3
2: 1 4 5
3: 1
4: 2 6
5: 2
6: 4
```

*Sample3_10nodes_structure2*
```
1: 2 7 8
2: 1 3 4
3: 2
4: 2 5 6
5: 4
6: 4
7: 1
8: 1 9 10
9: 8
10: 8
```

*Sample4_10nodes_structure2*
```
1: 2
2: 1 3 6
3: 2 4 5
4: 3
5: 3
6: 2 7 10
7: 6 8 9
8: 7
9: 7
10: 6
```

*Sample5_6nodes_structure3*
```
1: 2
2: 1 4 5
3: 5
4: 2
5: 2 3 6
6: 5
```

*Sample6_4nodes_structure4*
```
1: 2 3 4
2: 1
3: 1
4: 1
```

*Sample7_5nodes_structure5*
```
1: 2 3
2: 1
3: 1 4 5
4: 3
5: 3
```

*Sample8_8nodes_structure6*
```
1: 2 5 8
2: 1 3 4
3: 2
4: 2
5: 1 6 7
6: 5
7: 5
8: 1
```

*Sample9_Empty*
```

```

*Sample10_invalid_data*
```
(((1ss": 2 1
2:fg 1  5

5: 2 6 acb 1
6:]\]-\ -5
```
## 4.2 Тесты
Тестовый класс `TreeTest` по очереди запускает все тесты, выводит их результаты и считает кол-во успешных и неуспешных.
```java
public static void main(String[] args) {
        TreeTest tt = new TreeTest();
        System.setOut(new PrintStream(new ByteArrayOutputStream()));
        tt.out.println("\nTesting class {isomorphismoftrees.Tree}");
        tt.out.println("---------------------------------------");
        tt.testIsomorphicStruct1();
        tt.testIsomorphicStruct2();
        tt.testNonIsomorphicStruct1Struct3();
        tt.testNonIsomorphicDifferentQuantityNodes();
        tt.testIsomorphicItself();
        tt.testIsomorphicEmpty();
        tt.testIsomorphicEmptyStruct5();
        tt.testNonExistentFile();
        tt.testInvalidData();
        tt.out.println("---------------------------------------");
        tt.out.println("Successful tests: " + tt.successCount);
        if (tt.failureCount > 0){
            System.err.println("Failed tests: " + tt.failureCount);
        } else {
            tt.out.println("Failed tests: " + tt.failureCount);
        }
    }
```
`testIsomorphicStruct1()` - проверяет деревья с одинаковой структурой:

- На вход - *Sample1*, *Sample2*.
- Ожидаемый результат: `true` - деревья изоморфны.

`testIsomorphicStruct2()` - проверяет деревья с одинаковой структурой:

- На вход - *Sample3*, *Sample4*.
- Ожидаемый результат: `true` - деревья изоморфны.

`testNonIsomorphicStruct1Struct3()` - проверяет деревья с разной структурой:

- На вход - *Sample1*, *Sample5*.
- Ожидаемый результат: `false` - деревья  не изоморфны.

`testNonIsomorphicDifferentQuantityNodes()` - проверяет деревья с разным количеством узлов:

- На вход - *Sample7*, *Sample8*.
- Ожидаемый результат: `false` - деревья не изоморфны.

`testIsomorphicItself()` - проверяет один и тот же объект дерева:

- На вход - *Sample8*.
- Ожидаемый результат: `true` - дерево изоморфно самому себе.

`testIsomorphicEmpty()` - проверяет пустые деревья

- На вход - *Sample9*, *Sample9*.
- Ожидаемый результат: `true` - деревья изоморфны.

`testIsomorphicEmptyStruct5()` - проверяет пустое и непустое деревья:

- На вход - *Sample9*, *Sample7*.
- Ожидаемый результат: `false` - деревья не изоморфны.

`testNonExistentFile()` - пытается считать данные из несуществующего файла:

- На вход - *not_exist* (такого файла нет).
- Ожидаемый результат: `"src/resources/not_exist (Нет такого файла или каталога)\n"` - нет такого файла.

`testInvalidData()` - пытается считать некорректные данные:

- На вход - *Sample10*.
- Ожидаемый результат: `"Invalid data tree have loop. File: src/resources/Sample10_invalid_data\n"` - некорректные данные.

## 4.3 Вывод
Тестируется класс `Tree`:
- успешных пройденных тестов `9`
- проваленных тестов `0`
```
Testing class {isomorphismoftrees.Tree}
---------------------------------------
Success: testIsomorphicStruct1 - are isomorphic, same quantity nodes and structure
Success: testIsomorphicStruct2 - are isomorphic, same quantity nodes and structure
Success: testNonIsomorphicStruct1Struct3 - aren't isomorphic, different structure
Success: testNonIsomorphicDifferentQuantityNodes - aren't isomorphic, different quantity nodes
Success: testIsomorphicItself - is isomorphic, check itself
Success: testIsomorphicEmpty - are isomorphic, both empty
Success: testIsomorphicEmptyStruct5 - aren't isomorphic, one of them is empty
Success: testNonExistentFile - print to error stream not exist file
Success: testInvalidData - print to error stream file contains invalid data
---------------------------------------
Successful tests: 9
Failed tests: 0
```

# Иссточники
1. (ntuit.ru/studies/courses/58/58/lecture/1730?page=2#:~:text=Два%20корневых%20дерева%20называются%20изоморфными,одного%20дерева%20в%20корень%20другого)
2. (https://ru.algorithmica.org/cs/hashing/isomorphism/)
3. (https://www.youtube.com/watch?v=RI9UjijHqow&t=2875s)
4. (https://wiki.algocode.ru/index.php?title=%D0%A5%D0%B5%D1%88%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5_%D0%BA%D0%BE%D1%80%D0%BD%D0%B5%D0%B2%D1%8B%D1%85_%D0%B4%D0%B5%D1%80%D0%B5%D0%B2%D1%8C%D0%B5%D0%B2)
5. (https://logic.pdmi.ras.ru/~elena/ulanova-sum.pdf)
6. (https://ru.wikipedia.org/wiki/%D0%A2%D0%B5%D0%BE%D1%80%D0%B8%D1%8F_%D0%B3%D1%80%D0%B0%D1%84%D0%BE%D0%B2)
7. (http://algolist.ru/ds/)
8. Зимняя школа по программированию, Харьков, 2013.
9. (https://math.fandom.com/ru/wiki/%D0%98%D0%B7%D0%BE%D0%BC%D0%BE%D1%80%D1%84%D0%B8%D0%B7%D0%BC)
10. (https://otus.ru/journal/derevo-kak-struktura-dannyh/)
