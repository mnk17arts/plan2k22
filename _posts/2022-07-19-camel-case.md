---
layout: post
title: Camel Case                      
summary:
tags:
    - trie
    - strings
    - geeksforgeeks
    - cpp
    - medium
minute: 10 min
---

## Problem Statement - [*link*](https://practice.geeksforgeeks.org/batch-problems/camel-case04234120/0/?t#)  

Given a dictionary of words dict where each word follows CamelCase notation, print all words in the dictionary that match with a given pattern consisting of uppercase characters only.
CamelCase is the practice of writing compound words or phrases such that each word or abbreviation begins with a capital letter. Common examples include: “PowerPoint” and “WikiPedia”, “GeeksForGeeks”, “CodeBlocks”, etc.

Note: The order should be such that the output strings should be sorted by the lexicographic order of their abbreviations. For strings with same abbreviations the strings should be sorted by the usual lexicographic order. So, if Output Strings are Hi and HelloWorld, Hi should come first as H lexiographically is smaller than HW.



**Your Task:** 

Complete `findAllWords()` function and print as mentioned. If the pattern is not found, print "`No match found`" (without quotes) in the function itself. The new line is provided by the driver code.


**Expected Time Complexity:** `O(N * WORD_LEN)`              
**Expected Auxiliary Space:** `O(N * WORD_LEN)`



### Examples

**Example 1:**   
```
Input:
n = 8
dict[] = {Hi,Hello,HelloWorld,HiTech
HiGeek,HiTechWorld,HiTechCity,HiTechLab}
pattern = HA
Output: No match found
```

**Example 2:**   
```
Input:
n = 3
dict[]={WelcomeGeek,WelcomeToGeeksForGeeks
GeeksForGeeks}
pattern = WTG
Output: WelcomeToGeeksForGeeks
Explanation: WTG occurs in
WelcomeToGeeksForGeeks.
```

### Constraints

+ `1 ≤ N <= 100`
+ `1 <= length of pattern <= length of string <= 100`   


## Solutions

```cpp
struct TrieNode {
	TrieNode* children[ALPHABET_SIZE];
	bool isLeaf;
	vector<string> word;
};

TrieNode* getNewTrieNode(void) {
	TrieNode* pNode = new TrieNode;
	if (pNode) {
		pNode->isLeaf = false;
		for (int i = 0; i < ALPHABET_SIZE; i++)
			pNode->children[i] = NULL;
	}
	return pNode;
}

void insert(TrieNode* root, string word)    {
	int index;
	TrieNode* pCrawl = root;
	for (int level = 0; level < word.length(); level++)	{
		if (islower(word[level]))
			continue;
		index = int(word[level]) - 'A';
		if (!pCrawl->children[index])
			pCrawl->children[index] = getNewTrieNode();
		pCrawl = pCrawl->children[index];
	}
	pCrawl->isLeaf = true;
	(pCrawl->word).push_back(word);
}

void printAllWords(TrieNode* root) {
	if (root->isLeaf)	{
		sort((root->word).begin(), (root->word).end());
		for(string str : root->word)
			cout << str<<" ";
	}
	for (int i = 0; i < ALPHABET_SIZE; i++)	{
		TrieNode* child = root->children[i];
		if (child)
			printAllWords(child);
	}
}

bool search(TrieNode* root, string pattern) {
	int index;
	TrieNode* pCrawl = root;
	for (int level = 0; level < pattern.length(); level++)	{
		index = int(pattern[level]) - 'A';
		if (!pCrawl->children[index])
			return false;
		pCrawl = pCrawl->children[index];
	}
	printAllWords(pCrawl);
	return true;
}


class Solution
{
    public:
    void findAllWords(vector<string> dict, string pattern)    {
    	TrieNode* root = getNewTrieNode();
    	for (string word : dict)
    		insert(root, word);
    	if (!search(root, pattern))
    		cout << "No match found";
    }
};
```

