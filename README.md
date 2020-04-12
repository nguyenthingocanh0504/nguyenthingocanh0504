# nguyenthingocanh0504
how to user github
#include<bits/stdc++.h>
using namespace std;
class HANG
{
	string mahang,tenhang;
	long dongia;
	long soluong;
	public:
		void nhap();
		void xuat();
		long long thanhtien()
		{
			return soluong*dongia;
		}
		friend class PHIEU;
};
class PHIEU
{
	string maphieu,nguoiLP,ngay,khach;
	HANG x[30];
	int n;
	public:
		void nhap();
		void xuat();
};
void HANG::nhap()
{
	cout<<"Nhap ma hang: ";
	cin.ignore();
	getline(cin,mahang);
	cout<<"nhap ten hang: ";
	getline(cin,tenhang);
	cout<<"nhao don gia: ";
	cin>>dongia;
	cout<<"nhap so luong: ";
	cin>>soluong;
}
void HANG::xuat()
{
	cout<<"\t"<<left<<setw(10)<<mahang<<setw(10)<<tenhang<<setw(10)<<dongia<<setw(10)<<soluong<<setw(10)<<thanhtien()<<endl;
}
void PHIEU::nhap()
{
	cout<<"nhap ma phieu: ";
	cin.ignore();
	getline(cin,maphieu);
	cout<<"nhap nguoi thanh lap: ";
	getline(cin,nguoiLP);
	cout<<"nhap ngay lap phieu(d/m/y): ";
	getline(cin,ngay);
	cout<<"nhap ten khach hang: ";
	getline(cin,khach);
	cout<<"nhap so mat hang: ";
	cin>>n;
	for(int i=0;i<n;i++)
	{
		cout<<"nhap mat hang thu "<<i+1<<":\n";
		x[i].nhap();
	}
}
void PHIEU::xuat()
{
	cout<<"MA PHIEU: "<<maphieu<<endl;
	cout<<"Nguoi lap phieu: "<<nguoiLP;
	cout<<"\nNgay lap phieu: "<<ngay;
	cout<<"\nKhach hang: "<<khach<<endl;
	cout<<"\t"<<left<<setw(10)<<"ma hang"<<setw(10)<<"ten hang"<<setw(10)<<"don gia"<<setw(10)<<"so luong"<<setw(10)<<"thanh tien"<<endl;
	for(int i=0;i<n;i++)
	{
		x[i].xuat();
	}
	long long s=0;
	for(int i=0;i<n;i++)
	{
		s=s+x[i].thanhtien();
	}
	cout<<"\t\t\t\ttong tien:"<<s;
	int max=0;
	int dem=0;
	for(int i=0;i<n;i++)
	{
		if(x[i].soluong>max)
		{
			max=x[i].soluong;
		}
	}
	for(int i=0;i<n;i++)
	{
		if(x[i].soluong==max)
		{
			dem++;
		}
	}
	cout<<"\n\n===SO MAT HANG CO SO LUONG MUA MAX: "<<dem;
	for(int i=0;i<n-1;i++)
	{
		for(int j=i+1;j<n;j++)
		{
			if(x[i].thanhtien()>x[j].thanhtien())
			{
				HANG tg=x[i];
				x[i]=x[j];
				x[j]=tg;
			}
		}
	}
	cout<<"\n===TANG DAN THANH TIEN===\n";
	cout<<"MA PHIEU: "<<maphieu<<endl;
	cout<<"Nguoi lap phieu: "<<nguoiLP;
	cout<<"\nNgay lap phieu: "<<ngay;
	cout<<"\nKhach hang: "<<khach<<endl;
	cout<<"\t"<<left<<setw(10)<<"ma hang"<<setw(10)<<"ten hang"<<setw(10)<<"don gia"<<setw(10)<<"so luong"<<setw(10)<<"thanh tien"<<endl;
	for(int i=0;i<n;i++)
	{
		x[i].xuat();
	}
	for(int i=0;i<n;i++)
	{
		s=s+x[i].thanhtien();
	}
	cout<<"\t\t\t\ttong tien:"<<s;
	int vt;
	do
	{
	cout<<"\nnhap vi tri can chen: ";
	cin>>vt;
	}
	while(vt<=0||vt>n);
	HANG h;
	cout<<"\nnhap mat hang muon chen:\n";
	h.nhap();
	for(int i=n;i>=vt;i--)
		x[i]=x[i-1];
		x[vt-1]=h;
		n++;
	cout<<"\n===THONG TIN SAU KHI CHEN===\n";
	cout<<"MA PHIEU: "<<maphieu<<endl;
	cout<<"Nguoi lap phieu: "<<nguoiLP;
	cout<<"\nNgay lap phieu: "<<ngay;
	cout<<"\nKhach hang: "<<khach<<endl;
	cout<<"\t"<<left<<setw(10)<<"ma hang"<<setw(10)<<"ten hang"<<setw(10)<<"don gia"<<setw(10)<<"so luong"<<setw(10)<<"thanh tien"<<endl;
	for(int i=0;i<n;i++)
	{
		x[i].xuat();
	}
	for(int i=0;i<n;i++)
	{
		s=s+x[i].thanhtien();
	}
	cout<<"\t\t\t\ttong tien:"<<s;
}
int main()
{
	PHIEU p;
	p.nhap();
	cout<<"\n=====thong tin phieu=====\n";
	p.xuat();
}
