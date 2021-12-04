---
layout: post
title: Stream of Characters
summary:
tags:
    - array
    - string
    - trie
    - leetcode
    - cpp
    - hard
minute: 10 min
---

## Problem Statement - [*link*](https://leetcode.com/problems/stream-of-characters)  

Design an algorithm that accepts a stream of characters and checks if a suffix of these characters is a string of a given array of strings `words`.

For example, if `words = ["abc", "xyz"]` and the stream added the four characters (one by one) `'a'`, `'x'`, `'y'`, and `'z'`, your algorithm should detect that the suffix `"xyz"` of the characters `"axyz"` matches `"xyz"` from words.

Implement the `StreamChecker` class:

+ `StreamChecker(String[] words)` Initializes the object with the strings array `words`.
+ `boolean query(char letter)` Accepts a new character from the stream and returns `true` if any non-empty suffix from the stream forms a word that is in `words`.

### Examples

**Example 1:**   
```
Input
["StreamChecker", "query", "query", "query", "query", "query", "query", "query", "query", "query", "query", "query", "query"]
[[["cd", "f", "kl"]], ["a"], ["b"], ["c"], ["d"], ["e"], ["f"], ["g"], ["h"], ["i"], ["j"], ["k"], ["l"]]
Output
[null, false, false, false, true, false, true, false, false, false, false, false, true]

Explanation
StreamChecker streamChecker = new StreamChecker(["cd", "f", "kl"]);
streamChecker.query("a"); // return False
streamChecker.query("b"); // return False
streamChecker.query("c"); // return False
streamChecker.query("d"); // return True, because 'cd' is in the wordlist
streamChecker.query("e"); // return False
streamChecker.query("f"); // return True, because 'f' is in the wordlist
streamChecker.query("g"); // return False
streamChecker.query("h"); // return False
streamChecker.query("i"); // return False
streamChecker.query("j"); // return False
streamChecker.query("k"); // return False
streamChecker.query("l"); // return True, because 'kl' is in the wordlist
```

### Constraints
+ `1 <= words.length <= 2000`
+ `1 <= words[i].length <= 2000`
+ `words[i]` consists of lowercase English letters.
+ letter is a lowercase English letter.
+ At most `4 * 10^4` calls will be made to query.

## Solutions

```cpp
class StreamChecker {
private:   
    class Trie {   // Trie construction
    public:
        bool is_wordEnd;
        Trie* children[26];
        Trie() {
            this->is_wordEnd = false;
            for(int i=0;i<26;i++)
                this->children[i] = NULL;
        }
        
        void insert(string word) {
            
            reverse(word.begin(), word.end());  //gonna insert in reverse order
            
            Trie* node = this;
            
            for(int i=0;i<word.length();i++){
                int idx = word[i] - 'a';
                if (node->children[idx] == NULL)node->children[idx] = new Trie();
                node = node->children[idx];
            }
            node->is_wordEnd = true;
        }
    };
    
    Trie trie; // will store all the words provided !!
    vector<char>queries; //will store the stream of characters to match with the words given !!
    int max_length=0; //gonna store the length of longest word 
    
public:
    StreamChecker(vector<string>& words) {
        for (auto word: words){
            trie.insert(word);  //inserting words into trie
            if(word.size()>max_length)max_length=word.size(); //keep the track of max_length so that can maintain the length of StreamChecker in future !!
          }
    }
    
    bool query(char letter) {
        
        queries.insert(queries.begin(), letter);//inserting the incoming char in the queries vector at the front(), so that reverse order is maintained here too !!
        
        if (queries.size() > max_length)  // That's why we maintained max_length, because the 
            queries.pop_back();           // longest query that can match the word is never gonna be longer than the length of the longest word in the trie... So we pop() from the back !!
        
        Trie* cur = &trie;
        for (auto it = queries.begin(); it!=queries.end();++it)
        {
            if (cur->is_wordEnd) return true;
            if (cur->children[*it -'a'] == NULL) return false;
            cur = cur->children[*it-'a'];
        }
        return cur->is_wordEnd;
    }
    
};
```

