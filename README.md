# Location and Cost
_Observing trends in data between Manchester CCG's, Greater Manchester Mental Health NHS FT, and Manchester University NHS FT_
with open('./data/hero-network.csv', 'r') as f:
    data = csv.reader(f)
    headers = next(data)
    for row in tqdm(data):
        G.add_node(row[0]) #superhero in first column
        G.add_node(row[1]) #superhero in second column
        if G.has_edge(row[0], row[1]):
            # edge already exists, increase weight by one
            G[row[0]][row[1]]['weight'] += 1
        else:
            # add new edge with weight 1
            G.add_edge(row[0], row[1], weight = 1)
            G_nodes = G.number_of_nodes()
G_edges = G.number_of_edges()
print("Nodes = 10758", G_nodes, " Edges =500,000 ",G_edges)
