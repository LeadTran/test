#include <iostream>
using namespace std;
const int MAX = 50;
struct mang1Chieu {
	int list[MAX];
	int n;
};
void nhap(mang1Chieu& a);
void xuat(mang1Chieu a);
bool checkNT(int k);
int timMin(mang1Chieu a);
void xuatNTGiamDan(mang1Chieu a);
void nhap(mang1Chieu& a) {
	cout << "\nNhap so phan tu :";
	cin >> a.n;
	for (int i = 0; i < a.n; i++) {
		cout << "a[" << i << "]: ";
		cin >> a.list[i];
	}
}
void xuat(mang1Chieu a) {
	for (int i = 0; i < a.n; i++) {
		cout << a.list[i] << " ";
	}
}
bool checkNT(int k) {
	if (k < 2) {
		return 0;
	}
	for (int i = 2; i < k; i++) {
		if (k % i == 0) {
			return 0;
		}
	}
	return 1;
}
int timMin(mang1Chieu a) {
	int flag = 0;
	int min = 0;
	for (int i = 0; i < a.n; i++) {
		if (checkNT(a.list[i]) == 1) {
			if (flag == 0) {
				min = a.list[i];
				flag = 1;
			}
			else
				if (min > a.list[i]) {
					min = a.list[i];
				}
		}
	}
	return min;
}
void xuatNTGiamDan(mang1Chieu a) {
	mang1Chieu b;
	b = a;
	int min = 0;
	for (int i = 0; i < b.n; i++) {
		b.list[i] = 1;
	}
	for (int i = a.n - 1; i > 0; i--) {
		if (checkNT(a.list[i]) < checkNT(a.list[i - 1])) {
			b.list[i - 1] = b.list[i] + 1;
		}
	}
	cout << "\nDay b: ";
	xuat(b);
	int number = timMin(b);
	for (int i = 0; i < b.n; i++) {
		if (b.list[i] == number) {
			cout << "\nMang nguyen to giam dan it nhat la: ";
			for (int j = i; j < number + i; j++) {
				cout << a.list[j] << " ";
			}
		}
	}
}
void main() {
	mang1Chieu a;
	nhap(a);
	cout << "\nDay so vua nhap vao la : ";
	xuat(a);
	xuatNTGiamDan(a);
	system("pause");
}
