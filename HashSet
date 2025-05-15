package Hash;

public class HashSet
{
    private final int COEFFICIENT = 601;
    private final int DEFAULTCAPACITY = 16;
    private final double LOADFACTOR = 0.75;

    private Node[] table;
    private int size;

    public HashSet()
    {
        table = new Node[DEFAULTCAPACITY];
        size = 0;
    }

    public void add(int value)
    {
        if (contains(value))
            return;

        if (size >= table.length * LOADFACTOR)
            resize();

        var hash = getHash(value);
        table[hash] = new Node(value, table[hash]);
        size++;
    }

    public void remove(int value)
    {
        var hash = getHash(value);
        var node = table[hash];
        Node prev = null;

        while(node != null)
        {
            if(node.value == value)
            {
                if(prev == null)
                    table[hash] = node.next;
                else
                    prev.next = node.next;

                size--;
                return;
            }
            prev = node;
            node = node.next;
        }
    }

    public boolean contains(int value)
    {
        var hash = getHash(value);
        var node = table[hash];

        while(node != null)
        {
            if (node.value == value)
            {
                return true;
            }
            node = node.next;
        }

        return false;
    }

    private void resize()
    {
        var oldTable = table;
        table = new Node[oldTable.length * 2];
        size = 0;

        for(var node : oldTable)
        {
            while(node != null)
            {
                add(node.value);
                node = node.next;
            }
        }
    }

    private int getHash(int value)
    {
        return Math.abs(value * COEFFICIENT) % table.length;
    }

    private static class Node
    {
        int value;
        Node next;
        Node(int value, Node next)
        {
            this.value = value;
            this.next = next;
        }
    }
}
