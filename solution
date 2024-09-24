#include <string>
#include <vector>
#include <algorithm>
using namespace std;

// Trie Node structure
class TrieNode {
public:
    unordered_map<char, TrieNode*> children;
    bool isEndOfWord;
    
    TrieNode() : isEndOfWord(false) {}
};

// Trie structure for storing the string representations
class Trie {
public:
    TrieNode* root;
    
    Trie() {
        root = new TrieNode();
    }

    // Insert a string into the Trie
    void insert(const string& word) {
        TrieNode* node = root;
        for (char ch : word) {
            if (node->children.find(ch) == node->children.end()) {
                node->children[ch] = new TrieNode();
            }
            node = node->children[ch];
        }
        node->isEndOfWord = true;
    }

    // Find the length of the longest common prefix for a given string
    int findLongestPrefix(const string& word) {
        TrieNode* node = root;
        int count = 0;

        for (char ch : word) {
            if (node->children.find(ch) != node->children.end()) {
                node = node->children[ch];
                count++;
            } else {
                break;  // Stop if we reach a character not in the Trie
            }
        }

        return count;
    }
};

class Solution {
public:
    int longestCommonPrefix(vector<int>& arr1, vector<int>& arr2) {
        Trie trie;
        int ans = 0;

        // Step 1: Insert all string representations of arr1 into the Trie
        for (int num : arr1) {
            trie.insert(to_string(num));
        }

        // Step 2: For each number in arr2, find the longest common prefix using the Trie
        for (int num : arr2) {
            string str2 = to_string(num);
            ans = max(ans, trie.findLongestPrefix(str2));
        }

        return ans;
    }
};
