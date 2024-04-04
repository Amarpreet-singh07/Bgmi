# Bgmi
using System;
using System.Collections.Generic;

// Enum for different types of BGMI players
public enum PlayerType
{
    Beginner,
    Intermediate,
    Advanced
}

// Base class for BGMI players
public class BGMIPlayer
{
    public string Name { get; set; }
    public PlayerType Type { get; set; }

    public BGMIPlayer(string name, PlayerType type)
    {
        Name = name;
        Type = type;
    }

    public void Play()
    {
        Console.WriteLine($"{Name} is playing BGMI.");
    }
}

// Derived class representing a squad member
public class SquadMember : BGMIPlayer
{
    public SquadMember(string name, PlayerType type) : base(name, type)
    {
    }

    public void Communicate()
    {
        Console.WriteLine($"{Name} is communicating with squad members.");
    }
}

// Derived class representing a squad leader
public class SquadLeader : SquadMember
{
    public SquadLeader(string name, PlayerType type) : base(name, type)
    {
    }

    public void Lead()
    {
        Console.WriteLine($"{Name} is leading the squad.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Single Inheritance
        BGMIPlayer player1 = new BGMIPlayer("John", PlayerType.Beginner);
        player1.Play();

        // Multiple Inheritance
        SquadMember player2 = new SquadMember("Alice", PlayerType.Intermediate);
        player2.Play();
        player2.Communicate();

        // Hierarchical Inheritance
        SquadLeader player3 = new SquadLeader("Bob", PlayerType.Advanced);
        player3.Play();
        player3.Communicate();
        player3.Lead();
        
        // Using Enum
        Console.WriteLine($"{player1.Name} is a {player1.Type} player.");
        Console.WriteLine($"{player2.Name} is a {player2.Type} player.");
        Console.WriteLine($"{player3.Name} is a {player3.Type} player.");

        // Using Collections
        List<BGMIPlayer> players = new List<BGMIPlayer>();
        players.Add(player1);
        players.Add(player2);
        players.Add(player3);

        foreach (var player in players)
        {
            Console.WriteLine($"{player.Name} is playing BGMI.");
        }
    }
}
