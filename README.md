# Recommendations-
#include <iostream>
#include <vector>
using namespace std;

struct Article {
    string title;
    string category;
    int views;
};
void addArticle(vector<Article> &articles) {
    Article a;
    cin.ignore();

    cout << "Enter title: ";
    getline(cin, a.title);

    cout << "Enter category: ";
    getline(cin, a.category);

    a.views = 0;
    articles.push_back(a);

    cout << "Article added!\n";
}
void showArticles(const vector<Article> &articles) {
    cout << "\nAll Articles:\n";
    for (int i = 0; i < articles.size(); i++) {
        cout << i+1 << ". " << articles[i].title
             << " (" << articles[i].category << ") "
             << "Views: " << articles[i].views << endl;
    }
}

void recommend(vector<Article> &articles) {
    string interest;
    cin.ignore();

    cout << "Enter your interest: ";
    getline(cin, interest);

    cout << "\nRecommended:\n";
    bool found = false;

    for (auto &a : articles) {
        if (a.category == interest) {
            cout << "- " << a.title << endl;
            a.views++; 
            found = true;
        }
    }

    if (!found)
        cout << "No matching articles.\n";
}

int main() {
    vector<Article> articles = {
        {"AI Trends", "Tech", 0},
        {"Cricket Match", "Sports", 0}
    };

    int choice;

    do {
        cout << "\n1.Add 2.View 3.Recommend 4.Exit\n";
        cout << "Choice: ";
        cin >> choice;

        switch (choice) {
            case 1: addArticle(articles); break;
            case 2: showArticles(articles); break;
            case 3: recommend(articles); break;
            case 4: cout << "Bye!\n"; break;
            default: cout << "Invalid!\n";
        }

    } while (choice != 4);

    return 0;
}
