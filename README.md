###### LFZzz
***markwodn使用***
#### 啦啦啦
  i二到几点
  ```
  #include<string>
using namespace std;
class telMue
    {
        public:
            friend istream& operator>>(istream&, telMue&);
            friend ostream& operator<<(ostream&, telMue&);
            telMue();
            void setres(int _res);
            int getres();
            void setName(string _name);
            string getName();
            void setTel(string _tel,int i);
            string getTel(int i);
        private:
            int m_iRes;
            int m_iCount;
            string m_strName;
            string *m_strTel;
    };
```

