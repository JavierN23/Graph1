Create a theoretical graph:


![Graph1 drawio (1)](https://github.com/user-attachments/assets/3c5bc7e7-26e4-4f72-89fe-a8fb1f5f7b29)

Apply breadth and depth-first search algorithms using C++.


    #include <iostream>
    #include <map>
    #include <vector>
    #include <queue>
    #include <stack>
    #include <unordered_set>

    using namespace std;

    int main() {

    map<char, vector<char>> graph;    

    graph['A'] = {'B', 'C'};
    graph['B'] = {'A', 'D', 'E'};
    graph['C'] = {'A', 'F'};
    graph['D'] = {'B'};
    graph['E'] = {'B'};
    graph['F'] = {'C'};
    
    // BFS
    queue<char> q;
    unordered_set<char> visited;

    cout << "BFS: ";
    q.push('A');
    visited.insert('A');

    while (!q.empty()) {
        char current = q.front();
        q.pop();
        cout << current << " ";

        for (char neighbor : graph[current]) {
            if (!visited.count(neighbor)) {
                q.push(neighbor);
                visited.insert(neighbor);
            }
        }
    }
    cout << endl;

    // DFS
    stack<char> s;
    visited.clear();

    cout << "DFS: ";
    s.push('A');

    while (!s.empty()) {
        char current = s.top();
        s.pop();

        if (!visited.count(current)) {
            cout << current << " ";
            visited.insert(current);

            for (char neighbor : graph[current]) {
                if (!visited.count(neighbor)) {
                    s.push(neighbor);
                }
            }
        }
    }
    cout << endl;

    return 0;
    }
Compare both search algorithms in the context of Big O notations.
Breadth Search Algorithm is good at short path. It isn't as through as the Depth-First Algorithm since that algorithm search each individual path that is excessable. In terms of Time complexity they are both good but the first algorithm has a fast time complexity since it is finding the shortest path with the cost of missing some compared to the Depth-First Algorithm that goes through each path.

https://youtu.be/l2SNebbOAqk
