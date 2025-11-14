#include <stdio.h>
int main(){
    int a[10],i; float s=0;
    for(i=0;i<10;i++) scanf("%d",&a[i]);
    for(i=0;i<10;i++) s+=a[i];
    printf("%f",s/10);
}

 #include <stdio.h>
int main(){
    printf("*\n##\n***\n####");
}
#include <stdio.h>
int main(){
    int n,i,j,a[100],f=0;
    scanf("%d",&n);
    for(i=0;i<n;i++) scanf("%d",&a[i]);
    for(i=0;i<n;i++){
        for(j=i+1;j<n;j++){
            if(a[i]==a[j]){
                printf("%d",a[i]);
                f=1; break;
            }
        }
        if(f) break;
    }
    if(!f) printf("No Repeat");
}
#include <stdio.h>
int main(){
    int n,i,a[100],mx,mn;
    scanf("%d",&n);
    for(i=0;i<n;i++) scanf("%d",&a[i]);
    mx=mn=a[0];
    for(i=1;i<n;i++){
        if(a[i]>mx) mx=a[i];
        if(a[i]<mn) mn=a[i];
    }
    printf("%d %d",mx,mn);
}
#include <stdio.h>
int main(){
    int n,i,a[100];
    scanf("%d",&n);
    for(i=0;i<n;i++) scanf("%d",&a[i]);
    for(i=0;i<n;i++) if(i%2==1) a[i]*=a[i];
    for(i=0;i<n;i++) printf("%d ",a[i]);
}
#include <stdio.h>
int main(){
    int a[]={56,36,89,57,1,0,67,59},n=8,i,x,f=0;
    scanf("%d",&x);
    for(i=0;i<n;i++) if(a[i]==x){f=1;break;}
    if(f) printf("Found"); else printf("Not Found");
}
#include <stdio.h>
int main(){
    int n,i,a[100],l,h,m,x;
    scanf("%d",&n);
    for(i=0;i<n;i++) scanf("%d",&a[i]);
    scanf("%d",&x);
    l=0; h=n-1;
    while(l<=h){
        m=(l+h)/2;
        if(a[m]==x){printf("Found"); return 0;}
        else if(x<a[m]) h=m-1;
        else l=m+1;
    }
    printf("Not Found");
}
#include <stdio.h>
int main(){
    printf("Linear O(n)\nBinary O(log n)");
}
#include <stdio.h>
int main(){
    printf("Time O(n) slow for large data");
}
#include <stdio.h>
int main(){
    int n,i,j,a[100],t;
    scanf("%d",&n);
    for(i=0;i<n;i++) scanf("%d",&a[i]);
    for(i=0;i<n-1;i++)
        for(j=0;j<n-i-1;j++)
            if(a[j]>a[j+1]){
                t=a[j]; a[j]=a[j+1]; a[j+1]=t;
            }
    for(i=0;i<n;i++) printf("%d ",a[i]);
}
#include <stdio.h>
int main(){
    int n,i,j,a[100],t,m;
    scanf("%d",&n);
    for(i=0;i<n;i++) scanf("%d",&a[i]);
    for(i=0;i<n-1;i++){
        m=i;
        for(j=i+1;j<n;j++) if(a[j]>a[m]) m=j;
        t=a[i]; a[i]=a[m]; a[m]=t;
    }
    for(i=0;i<n;i++) printf("%d ",a[i]);
}
#include <stdio.h>
int main(){
    printf("%d",10);
}
#include <stdio.h>
int main(){
    int a[]={500,-20,30,14,50},n=5,i,j,m,t;
    for(i=0;i<n-1;i++){
        m=i;
        for(j=i+1;j<n;j++) if(a[j]<a[m]) m=j;
        t=a[i]; a[i]=a[m]; a[m]=t;
    }
    for(i=0;i<n;i++) printf("%d ",a[i]);
}
#include <stdio.h>
int main(){
    int n,i,j,k,a[100];
    scanf("%d",&n);
    for(i=0;i<n;i++) scanf("%d",&a[i]);
    for(i=1;i<n;i++){
        k=a[i];
        j=i-1;
        while(j>=0 && a[j]>k){a[j+1]=a[j]; j--;}
        a[j+1]=k;
    }
    for(i=0;i<n;i++) printf("%d ",a[i]);
}
#include <stdio.h>
int getmax(int a[],int n){
    int m=a[0],i;
    for(i=1;i<n;i++) if(a[i]>m) m=a[i];
    return m;
}
void countsort(int a[],int n,int e){
    int o[100],c[10]={0},i;
    for(i=0;i<n;i++) c[(a[i]/e)%10]++;
    for(i=1;i<10;i++) c[i]+=c[i-1];
    for(i=n-1;i>=0;i--){
        o[c[(a[i]/e)%10]-1]=a[i];
        c[(a[i]/e)%10]--;
    }
    for(i=0;i<n;i++) a[i]=o[i];
}
int main(){
    int n,a[100],i,m,e;
    scanf("%d",&n);
    for(i=0;i<n;i++) scanf("%d",&a[i]);
    m=getmax(a,n);
    for(e=1;m/e>0;e*=10) countsort(a,n,e);
    for(i=0;i<n;i++) printf("%d ",a[i]);
}
#include <stdio.h>
int main(){
    printf("3 5 7 1 9 8 4 6");
}
#include <stdio.h>
#include <stdlib.h>
struct node{int d; struct node*next;};
struct node*head=NULL;

void create(){
    int n,x,i;
    scanf("%d",&n);
    for(i=0;i<n;i++){
        scanf("%d",&x);
        struct node*t=malloc(sizeof(struct node));
        t->d=x; t->next=NULL;
        if(!head) head=t;
        else{
            struct node*p=head;
            while(p->next) p=p->next;
            p->next=t;
        }
    }
}

void insbeg(){
    int x; scanf("%d",&x);
    struct node*t=malloc(sizeof(struct node));
    t->d=x; t->next=head; head=t;
}

void insmid(){
    int pos,x,i; scanf("%d%d",&pos,&x);
    struct node*p=head;
    for(i=1;i<pos-1;i++) p=p->next;
    struct node*t=malloc(sizeof(struct node));
    t->d=x; t->next=p->next; p->next=t;
}

void insend(){
    int x; scanf("%d",&x);
    struct node*t=malloc(sizeof(struct node));
    t->d=x; t->next=NULL;
    if(!head) head=t;
    else{
        struct node*p=head;
        while(p->next) p=p->next;
        p->next=t;
    }
}

void delbeg(){
    if(head){struct node*t=head; head=head->next; free(t);}
}

void delmid(){
    int pos,i; scanf("%d",&pos);
    struct node*p=head;
    for(i=1;i<pos-1;i++) p=p->next;
    struct node*t=p->next;
    p->next=t->next;
    free(t);
}

void delend(){
    if(!head) return;
    if(!head->next){free(head); head=NULL; return;}
    struct node*p=head;
    while(p->next->next) p=p->next;
    free(p->next); p->next=NULL;
}

void display(){
    struct node*p=head;
    while(p){printf("%d ",p->d); p=p->next;}
}

void concat(struct node*h2){
    struct node*p=head;
    if(!head){head=h2; return;}
    while(p->next) p=p->next;
    p->next=h2;
}

void count(){
    int c=0; struct node*p=head;
    while(p){c++; p=p->next;}
    printf("%d",c);
}

void reverse(){
    struct node*p=head,*q=NULL,*r=NULL;
    while(p){
        r=q; q=p; p=p->next; q->next=r;
    }
    head=q;
}

void search(){
    int x; scanf("%d",&x);
    struct node*p=head;
    while(p){
        if(p->d==x){printf("Found"); return;}
        p=p->next;
    }
    printf("Not Found");
}

int main(){
    int ch;
    while(scanf("%d",&ch)){
        if(ch==1) create();
        else if(ch==2) insbeg();
        else if(ch==3) insmid();
        else if(ch==4) insend();
        else if(ch==5) delbeg();
        else if(ch==6) delmid();
        else if(ch==7) delend();
        else if(ch==8) display();
        else if(ch==9) count();
        else if(ch==10) reverse();
        else if(ch==11) search();
        else return 0;
    }
}
#include <stdio.h>
#include <stdlib.h>
struct node{int d; struct node*prev,*next;};
struct node*head=NULL;

void create(){
    int n,x,i; scanf("%d",&n);
    for(i=0;i<n;i++){
        scanf("%d",&x);
        struct node*t=malloc(sizeof(struct node));
        t->d=x; t->prev=t->next=NULL;
        if(!head) head=t;
        else{
            struct node*p=head;
            while(p->next) p=p->next;
            p->next=t; t->prev=p;
        }
    }
}

void display(){
    struct node*p=head;
    while(p){printf("%d ",p->d); p=p->next;}
}

void insert(){
    int pos,x,i; scanf("%d%d",&pos,&x);
    struct node*t=malloc(sizeof(struct node)); t->d=x;
    if(pos==1){
        t->next=head; t->prev=NULL;
        if(head) head->prev=t;
        head=t; return;
    }
    struct node*p=head;
    for(i=1;i<pos-1;i++) p=p->next;
    t->next=p->next; t->prev=p;
    if(p->next) p->next->prev=t;
    p->next=t;
}

void del(){
    int pos,i; scanf("%d",&pos);
    struct node*p=head;
    if(pos==1){
        head=head->next;
        if(head) head->prev=NULL;
        free(p); return;
    }
    for(i=1;i<pos;i++) p=p->next;
    p->prev->next=p->next;
    if(p->next) p->next->prev=p->prev;
    free(p);
}

void search(){
    int x; scanf("%d",&x);
    struct node*p=head;
    while(p){if(p->d==x){printf("Found"); return;} p=p->next;}
    printf("Not Found");
}

void count(){
    int c=0; struct node*p=head;
    while(p){c++; p=p->next;} printf("%d",c);
}

void reverse(){
    struct node*p=head,*t=NULL;
    while(p){t=p->prev; p->prev=p->next; p->next=t; p=p->prev;}
    if(t) head=t->prev;
}

int main(){
    int ch;
    while(scanf("%d",&ch)){
        if(ch==1) create();
        else if(ch==2) display();
        else if(ch==3) insert();
        else if(ch==4) del();
        else if(ch==5) search();
        else if(ch==6) count();
        else if(ch==7) reverse();
        else return 0;
    }
}
#include <stdio.h>
int s[8],top=-1;
void push(int x){if(top<7){s[++top]=x;}}
void pop(){if(top>=0) top--;}
int empty(){return top==-1;}
int full(){return top==7;}
int main(){
    push(10); push(20); pop(); push(25); push(50);
    push(70); pop(); pop(); push(100); pop();
    int i; for(i=0;i<=top;i++) printf("%d ",s[i]);
}
#include <stdio.h>
#include <ctype.h>
char s[100]; int top=-1;
void push(char x){s[++top]=x;}
char pop(){return s[top--];}
int p(char c){if(c=='+'||c=='-')return 1; if(c=='*'||c=='/')return 2; if(c=='^')return 3; return 0;}
int main(){
    char in[100],post[100]; int i=0,j=0;
    scanf("%s",in);
    while(in[i]){
        if(isalnum(in[i])) post[j++]=in[i];
        else if(in[i]=='(') push('(');
        else if(in[i]==')'){
            while(s[top]!='(') post[j++]=pop();
            pop();
        } else{
            while(top!=-1 && p(s[top])>=p(in[i])) post[j++]=pop();
            push(in[i]);
        }
        i++;
    }
    while(top!=-1) post[j++]=pop();
    post[j]=0;
    printf("%s",post);
}
#include <stdio.h>
#include <ctype.h>
int s[100],top=-1;
void push(int x){s[++top]=x;}
int pop(){return s[top--];}
int main(){
    char p[100]; int i;
    scanf("%s",p);
    for(i=0;p[i];i++){
        if(isdigit(p[i])) push(p[i]-'0');
        else{
            int b=pop(),a=pop();
            if(p[i]=='+') push(a+b);
            else if(p[i]=='-') push(a-b);
            else if(p[i]=='*') push(a*b);
            else if(p[i]=='/') push(a/b);
        }
    }
    printf("%d",pop());
}
#include <stdio.h>
#include <string.h>
#include <ctype.h>
int s[100],top=-1;
void push(int x){s[++top]=x;}
int pop(){return s[top--];}
int main(){
    char p[100]; int i;
    scanf("%[^\n]",p);
    int n=strlen(p);
    for(i=n-1;i>=0;i--){
        if(p[i]==' ') continue;
        if(isdigit(p[i])) push(p[i]-'0');
        else{
            int a=pop(),b=pop();
            if(p[i]=='+') push(a+b);
            else if(p[i]=='-') push(a-b);
            else if(p[i]=='*') push(a*b);
            else if(p[i]=='/') push(a/b);
        }
    }
    printf("%d",pop());
}
#include <stdio.h>
int q[10],f=0,r=-1;
void insert(int x){if(r<9) q[++r]=x;}
void del(){if(f<=r) f++;}
void disp(){int i; for(i=f;i<=r;i++) printf("%d ",q[i]);}
int main(){
    insert(10); insert(50); del(); insert(100); insert(20);
    del(); insert(25); insert(200); disp();
}
#include <stdio.h>
int q[10],f=-1,r=-1,n=10;
void insert(int x){
    if((r+1)%n==f) return;
    if(f==-1) f=0;
    r=(r+1)%n; q[r]=x;
}
void del(){
    if(f==-1) return;
    if(f==r){f=r=-1;}
    else f=(f+1)%n;
}
void disp(){
    if(f==-1) return;
    int i=f;
    while(1){
        printf("%d ",q[i]);
        if(i==r) break;
        i=(i+1)%n;
    }
}
int main(){
    insert(10); insert(20); insert(30);
    del(); disp();
}
#include <stdio.h>
#include <stdlib.h>
struct node{int d; struct node*l,*r;};
struct node*create(){
    int x; scanf("%d",&x);
    if(x==-1) return NULL;
    struct node*t=malloc(sizeof(struct node));
    t->d=x;
    t->l=create();
    t->r=create();
    return t;
}
void inorder(struct node*t){
    if(t){inorder(t->l); printf("%d ",t->d); inorder(t->r);}
}
struct node*search(struct node*t,int x){
    if(!t) return NULL;
    if(t->d==x) return t;
    struct node*p=search(t->l,x);
    if(p) return p;
    return search(t->r,x);
}
struct node*del(struct node*t,int x){
    if(!t) return NULL;
    if(x<t->d) t->l=del(t->l,x);
    else if(x>t->d) t->r=del(t->r,x);
    else{
        if(!t->l){struct node*temp=t->r; free(t); return temp;}
        if(!t->r){struct node*temp=t->l; free(t); return temp;}
        struct node*p=t->r;
        while(p->l) p=p->l;
        t->d=p->d;
        t->r=del(t->r,p->d);
    }
    return t;
}
int main(){
    struct node*root=create();
    inorder(root);
}
#include <stdio.h>
int main(){
    int n,i,j,a[10][10];
    scanf("%d",&n);
    for(i=0;i<n;i++)
        for(j=0;j<n;j++) scanf("%d",&a[i][j]);
    for(i=0;i<n;i++){
        for(j=0;j<n;j++) printf("%d ",a[i][j]);
        printf("\n");
    }
}
#include <stdio.h>
#include <stdlib.h>
struct node{int v; struct node*next;};
int main(){
    int n,e,i,x,y;
    scanf("%d%d",&n,&e);
    struct node*adj[n];
    for(i=0;i<n;i++) adj[i]=NULL;
    for(i=0;i<e;i++){
        scanf("%d%d",&x,&y);
        struct node*t=malloc(sizeof(struct node));
        t->v=y; t->next=adj[x]; adj[x]=t;
    }
    for(i=0;i<n;i++){
        struct node*p=adj[i];
        printf("%d:",i);
        while(p){printf("%d ",p->v); p=p->next;}
        printf("\n");
    }
}
