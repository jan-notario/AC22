internal class Program
{
    static Stack<string> pilaNaves = new Stack<string>();
    static Queue<string> colaNaves = new Queue<string>();
    static List<string> listaNaves = new List<string>();
    static Random random = new Random();

    static void Main(string[] args)
    {
        int accion;
        int contadorNaves = 0;

        do
        {
            MostrarMenu();
            accion = LeerEntero("Seleccione una opcion: ", 1, 7);

            switch (accion)
            {
                case 1:
                    CrearNave(ref contadorNaves);
                    break;
                case 2:
                    CambiarNombreNave();
                    break;
                case 3:
                    ListarTodasLasNaves();
                    break;
                case 4:
                    EliminarNave();
                    break;
                case 5:
                    EliminarTodasLasNaves();
                    break;
                case 6:
                    ListarNavesPorTipo();
                    break;
                case 7:
                    Console.WriteLine("Programa finalizado.");
                    break;
            }

            Console.WriteLine();
        } while (accion != 7);
    }

    static void MostrarMenu()
    {
        Console.WriteLine("=== SISTEMA DE FABRICACION DE NAVES ESTELARES ===");
        Console.WriteLine();
        Console.WriteLine("1. Crear nueva nave");
        Console.WriteLine("2. Cambiar nombre de una nave");
        Console.WriteLine("3. Listar todas las naves");
        Console.WriteLine("4. Eliminar una nave");
        Console.WriteLine("5. Eliminar todas las naves");
        Console.WriteLine("6. Listar naves por tipo");
        Console.WriteLine("7. Salir");
    }

    static int LeerEntero(string mensaje, int minimo, int maximo)
    {
        while (true)
        {
            Console.Write(mensaje);
            string entrada = Console.ReadLine();
            if (int.TryParse(entrada, out int valor) && valor >= minimo && valor <= maximo)
            {
                return valor;
            }

            Console.WriteLine($"Entrada invalida. Ingrese un numero entre {minimo} y {maximo}.");
        }
    }

    static string LeerTexto(string mensaje)
    {
        while (true)
        {
            Console.Write(mensaje);
            string texto = Console.ReadLine();
            if (!string.IsNullOrWhiteSpace(texto))
            {
                return texto.Trim();
            }

            Console.WriteLine("El texto no puede estar vacio.");
        }
    }

    static void CrearNave(ref int contadorNaves)
    {
        string[] tiposNave = { "HALCONMILENARIO", "CAZAESTELAR", "SUPERDESTRUCTOR", "YWING", "XWING" };
        string tipo = tiposNave[random.Next(tiposNave.Length)];
        int numero = random.Next(10, 100);
        string nombreNave = $"{tipo}-{numero}";

        if (tipo == "HALCONMILENARIO" || tipo == "CAZAESTELAR")
        {
            pilaNaves.Push(nombreNave);
            Console.WriteLine($"? Nave creada: {nombreNave} (Almacenada en PILA)");
        }
        else if (tipo == "SUPERDESTRUCTOR" || tipo == "YWING")
        {
            colaNaves.Enqueue(nombreNave);
            Console.WriteLine($"? Nave creada: {nombreNave} (Almacenada en COLA)");
        }
        else
        {
            listaNaves.Add(nombreNave);
            Console.WriteLine($"? Nave creada: {nombreNave} (Almacenada en LISTA)");
        }

        contadorNaves++;
    }

    static void CambiarNombreNave()
    {
        if (pilaNaves.Count == 0 && colaNaves.Count == 0 && listaNaves.Count == 0)
        {
            Console.WriteLine("No hay naves para renombrar.");
            return;
        }

        Console.WriteLine("Que estructura desea modificar?");
        Console.WriteLine("1. Pila");
        Console.WriteLine("2. Cola");
        Console.WriteLine("3. Lista");
        int opcion = LeerEntero("Seleccione: ", 1, 3);

        switch (opcion)
        {
            case 1:
                if (pilaNaves.Count == 0)
                {
                    Console.WriteLine("La pila no tiene naves.");
                    return;
                }
                RenombrarPila();
                break;
            case 2:
                if (colaNaves.Count == 0)
                {
                    Console.WriteLine("La cola no tiene naves.");
                    return;
                }
                RenombrarCola();
                break;
            case 3:
                if (listaNaves.Count == 0)
                {
                    Console.WriteLine("La lista no tiene naves.");
                    return;
                }
                RenombrarLista();
                break;
        }
    }

    static void RenombrarPila()
    {
        string[] naves = pilaNaves.ToArray();
        Console.WriteLine("=== NAVES EN PILA ===");
        for (int i = 0; i < naves.Length; i++)
        {
            string indicador = i == 0 ? " (tope)" : string.Empty;
            Console.WriteLine($"[{i}] {naves[i]}{indicador}");
        }

        int posicion = LeerEntero("Ingrese la posicion de la nave en la pila: ", 0, naves.Length - 1);
        string nuevoNombre = LeerTexto("Ingrese el nuevo nombre para la nave en la pila: ");
        string viejoNombre = naves[posicion];
        naves[posicion] = nuevoNombre;

        pilaNaves.Clear();
        for (int i = naves.Length - 1; i >= 0; i--)
        {
            pilaNaves.Push(naves[i]);
        }

        Console.WriteLine($"? Nave renombrada: {viejoNombre} ? {nuevoNombre}");
    }

    static void RenombrarCola()
    {
        string[] naves = colaNaves.ToArray();
        Console.WriteLine("=== NAVES EN COLA ===");
        for (int i = 0; i < naves.Length; i++)
        {
            string indicador = i == 0 ? " (frente)" : string.Empty;
            Console.WriteLine($"[{i}] {naves[i]}{indicador}");
        }

        int posicion = LeerEntero("Ingrese la posicion de la nave en la cola: ", 0, naves.Length - 1);
        string nuevoNombre = LeerTexto("Ingrese el nuevo nombre para la nave en la cola: ");
        string viejoNombre = naves[posicion];
        naves[posicion] = nuevoNombre;

        colaNaves.Clear();
        foreach (var nave in naves)
        {
            colaNaves.Enqueue(nave);
        }

        Console.WriteLine($" Nave renombrada: {viejoNombre} ? {nuevoNombre}");
    }

    static void RenombrarLista()
    {
        Console.WriteLine("=== NAVES EN LISTA ===");
        for (int i = 0; i < listaNaves.Count; i++)
        {
            Console.WriteLine($"[{i}] {listaNaves[i]}");
        }

        int indice = LeerEntero("Ingrese el indice de la nave en la lista: ", 0, listaNaves.Count - 1);
        string nuevoNombre = LeerTexto("Ingrese el nuevo nombre para la nave en la lista: ");
        string viejoNombre = listaNaves[indice];
        listaNaves[indice] = nuevoNombre;

        Console.WriteLine($"? Nave renombrada: {viejoNombre} ? {nuevoNombre}");
    }

    static void ListarTodasLasNaves(string titulo = "=== NAVES FABRICADAS ===")
    {
        Console.WriteLine(titulo);
        Console.WriteLine();

        Console.WriteLine("PILA (LIFO - Last In, First Out):");
        if (pilaNaves.Count == 0)
        {
            Console.WriteLine("(vacia)");
        }
        else
        {
            string[] navesPila = pilaNaves.ToArray();
            for (int i = 0; i < navesPila.Length; i++)
            {
                Console.WriteLine($"[{i}] {navesPila[i]}");
            }
        }

        Console.WriteLine();
        Console.WriteLine("COLA (FIFO - First In, First Out):");
        if (colaNaves.Count == 0)
        {
            Console.WriteLine("(vacía)");
        }
        else
        {
            string[] navesCola = colaNaves.ToArray();
            for (int i = 0; i < navesCola.Length; i++)
            {
                Console.WriteLine($"[{i}] {navesCola[i]}");
            }
        }

        Console.WriteLine();
        Console.WriteLine("LISTA (Acceso por índice):");
        if (listaNaves.Count == 0)
        {
            Console.WriteLine("(vacía)");
        }
        else
        {
            for (int i = 0; i < listaNaves.Count; i++)
            {
                Console.WriteLine($"[{i}] {listaNaves[i]}");
            }
        }
    }

    static void ListarNavesPorTipo()
    {
        Console.WriteLine("Ingrese el tipo de nave a listar:");
        Console.WriteLine("1. Pila (HALCONMILENARIO, CAZAESTELAR)");
        Console.WriteLine("2. Cola (SUPERDESTRUCTOR, YWING)");
        Console.WriteLine("3. Lista (XWING)");
        int opcion = LeerEntero("Seleccione: ", 1, 3);

        switch (opcion)
        {
            case 1:
                Console.WriteLine();
                Console.WriteLine("=== NAVES EN PILA ===");
                if (pilaNaves.Count == 0)
                {
                    Console.WriteLine("(vacia)");
                }
                else
                {
                    string[] navesPila = pilaNaves.ToArray();
                    for (int i = 0; i < navesPila.Length; i++)
                    {
                        string indicador = i == 0 ? " (tope)" : string.Empty;
                        Console.WriteLine($"[{i}] {navesPila[i]}{indicador}");
                    }
                }
                break;
            case 2:
                Console.WriteLine();
                Console.WriteLine("=== NAVES EN COLA ===");
                if (colaNaves.Count == 0)
                {
                    Console.WriteLine("(vacia)");
                }
                else
                {
                    string[] navesCola = colaNaves.ToArray();
                    for (int i = 0; i < navesCola.Length; i++)
                    {
                        string indicador = i == 0 ? " (frente)" : string.Empty;
                        Console.WriteLine($"[{i}] {navesCola[i]}{indicador}");
                    }
                }
                break;
            case 3:
                Console.WriteLine();
                Console.WriteLine("=== NAVES EN LISTA ===");
                if (listaNaves.Count == 0)
                {
                    Console.WriteLine("(vacia)");
                }
                else
                {
                    for (int i = 0; i < listaNaves.Count; i++)
                    {
                        Console.WriteLine($"[{i}] {listaNaves[i]}");
                    }
                }
                break;
        }
    }

    static void EliminarNave()
    {
        Console.WriteLine("Que estructura desea eliminar?");
        Console.WriteLine("1. Pila");
        Console.WriteLine("2. Cola");
        Console.WriteLine("3. Lista");
        int opcion = LeerEntero("Seleccione: ", 1, 3);

        switch (opcion)
        {
            case 1:
                if (pilaNaves.Count == 0)
                {
                    Console.WriteLine("La pila esta vacia.");
                    return;
                }
                string navePila = pilaNaves.Pop();
                Console.WriteLine($"? Nave eliminada de la pila: {navePila}");
                break;
            case 2:
                if (colaNaves.Count == 0)
                {
                    Console.WriteLine("La cola esta vacia.");
                    return;
                }
                string naveCola = colaNaves.Dequeue();
                Console.WriteLine($"? Nave eliminada de la cola: {naveCola}");
                break;
            case 3:
                if (listaNaves.Count == 0)
                {
                    Console.WriteLine("La lista esta vacia.");
                    return;
                }
                for (int i = 0; i < listaNaves.Count; i++)
                {
                    Console.WriteLine($"[{i}] {listaNaves[i]}");
                }
                int indice = LeerEntero("Ingrese el indice de la nave a eliminar: ", 0, listaNaves.Count - 1);
                string naveLista = listaNaves[indice];
                listaNaves.RemoveAt(indice);
                Console.WriteLine($"? Nave eliminada de la lista: {naveLista}");
                break;
        }
    }

    static void EliminarTodasLasNaves(bool mostrarConfirmacion = true)
    {
        if (mostrarConfirmacion)
        {
            string respuesta = LeerTexto("Esta seguro de eliminar todas las naves? (s/n): ").ToLower();
            if (respuesta != "s" && respuesta != "si")
            {
                Console.WriteLine("Operacion cancelada.");
                return;
            }
        }

        pilaNaves.Clear();
        colaNaves.Clear();
        listaNaves.Clear();
        Console.WriteLine("? Todas las naves han sido eliminadas.");
    }
}
