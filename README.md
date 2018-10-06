# Social-Network-Analysis
Basics of Social Network Analysis

Some concepts and terminologies required to perform a social network analysis:
1. A network is represented as graph, which shows links between each vertex(or node) and its neighbours.
2. A line indicating a link between vertices is called a edge.
3. A group of vertices that are mutually reachable by following edges on the graph is called a component.
4. The edges on the graph is called a component.
5. The edged followed from one node to another are called a path. 

Kinds of graphs:
1. Undirected Graph: An undirected graph is graph, i.e., a set of objects (called vertices or nodes) that are connected together, where all the edges are bidirectional.
2. Directed Graph: A directed graph is graph, i.e., a set of objects (called vertices or nodes) that are connected together, where all the edges are directed from one vertex to another.

Measurements of vertex(or node):
1. Vertex Density = No. of connections divided by total possible connections 
2. Vertex Degree = No. of links from each vertex
3. Clique = A group of vertices where all the possible links are present 

Pacakage used : "igraph"

Code:

#Undirected Graph 
graph1 <- graph_from_data_frame(g1, directed = FALSE, vertices = NULL)
plot(graph1)

#Plotting a new graph
g_full <- make_full_graph(8,directed = FALSE)
plot(g_full)

#Ring Graph
g_ring <- make_ring(12, directed = FALSE, mutual = FALSE, circular = TRUE)
plot(g_ring)

#Star Graph
g_star <- make_star(10, mode = c("in","out","mutual","undirected"), center = 1)
plot(g_star)

#Random generation algorithm
g_gnp <- sample_gnp(20, 0.3, directed = FALSE, loops = FALSE)
plot(g_gnp)

g_gnm <- sample_gnm(20, 50, directed = FALSE, loops = FALSE)
plot(g_gnm)

#Preferrential attachment
g_gpa <- sample_pa(15, power = 1)
plot(g_gpa)

degree(g_gpa) #No. of links from each vertex

betweenness(g_gpa) #Measure of betweenness of points

edge_density(g_gpa, loops = FALSE) #Calculate the network density

#Cliques
rgnp <- sample_gnp(20, 0.3, directed = FALSE, loops = FALSE)
plot(rgnp)
clique_num(rgnp) #to find the largest clique
cliques(rgnp, min = 4) #to find all the vertices with the similar cliques

#Components in a network graph
sgnp <- sample_gnp(30, 0.08, directed = FALSE, loops = FALSE)
plot(sgnp)
components(sgnp) #To find the components 

#Walk through the network graph
s1 <- sample_gnp(30, 0.08, directed = FALSE, loops = FALSE)
plot(s1)
random_walk(s1, 26, 8, stuck = 'return') 

#Storin and Downloading edgelist
p1 <- sample_gnp(30, 0.08) %>% set_vertex_attr("color", value = "yellow") %>% set_edge_attr("color", value = "green")
write.graph(p1, file = "rand_network.txt", format = "edgelist") #To get a "edgelist"
pdf("rand_network.txt") #To download the pdf format of edgelist
plot(p1)
dev.off()
