# best-repo-ever
public class contestEntry
        {
            public decimal rank{get;set;}
            public string name{get;set;}
        }
        
        map<string,contestEntry> entries = new map<string,contestEntry>();
        
        contestEntry entry1 = new contestEntry();
        entry1.rank = 5;
        entry1.name = 'Fraction';
        entries.put(entry1.name,entry1);
        
        contestEntry entry2 = new contestEntry();
        entry2.rank = 3;
        entry2.name = 'Bob';
        entries.put(entry2.name,entry2);
        
        contestEntry entry3 = new contestEntry();
        entry3.rank = 1;
        entry3.name = 'Jonathan';
        entries.put(entry3.name,entry3);
        
        contestEntry entry4 = new contestEntry();
        entry4.rank = 4;
        entry4.name = 'Sandy';
        entries.put(entry4.name,entry4);
        
        contestEntry entry5 = new contestEntry();
        entry5.rank = 2;
        entry5.name = 'Felix';
        entries.put(entry5.name,entry5);
        
        //oh no, these entries are all out of order. 
        system.debug(entries) ;
        
        //lets get sorting these guys. First we'll need a map to store the rank, and the contestEntry that rank is 
        //associated with
        map<decimal,string> rankToNameMap = new map<decimal,string>();
        
        for(contestEntry entry : entries.values())
        {
            rankToNameMap.put(entry.rank,entry.name);
        }
        //now lets put those ranks in a list
        list<decimal> ranksList = new list<decimal>();
        ranksList.addAll(rankToNameMap.keySet());
    
        //now sort them
        ranksList.sort();
        
        //ok, so now we have the ranks in order, we need to figure out who had that rank
        for(decimal rank : ranksList)
        {
            String thisEntryName = rankToNameMap.get(rank);    
            contestEntry thisEntry = entries.get(thisEntryName);
            system.debug(thisEntry);
        }