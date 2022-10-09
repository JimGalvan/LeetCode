# Design Browser History
## Problem
https://leetcode.com/problems/design-browser-history/

## Solution
```
class BrowserHistory {

    static class Page {
        Page prev;
        Page next;
        String url;
        
        Page(String url){
            this.url = url;
        }
    }
    
    Page currentPage;

    public BrowserHistory(String homepage) {
        this.currentPage = new Page(homepage);
    }
    
    public void visit(String url) {
        Page newPage = new Page(url);
        currentPage.next = newPage;
        newPage.prev = currentPage;
        currentPage = newPage;
    }
    
    public String back(int steps) {
            
        String currentUrl = currentPage.url;
        
        while (steps > 0){
            
            if (currentPage.prev == null){
                return currentUrl;
            }
            
            currentPage = currentPage.prev;
            currentUrl = currentPage.url;
            steps--;
        }
        
        return currentUrl;
    }
    
    public String forward(int steps) {
        String currentUrl = currentPage.url;
        
        while (steps > 0){
            
            if (currentPage.next == null){
                return currentUrl;
            }
            
            currentPage = currentPage.next;
            currentUrl = currentPage.url;
            steps--;
        }
        
        return currentUrl;
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * BrowserHistory obj = new BrowserHistory(homepage);
 * obj.visit(url);
 * String param_2 = obj.back(steps);
 * String param_3 = obj.forward(steps);
 */
 
 ```
