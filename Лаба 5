#include <iostream>
#include <math.h>




using namespace std;
double funk(double x)
{
	double time_t;
	time_t = (0.1 * pow(x, 2)) / (log10(x));
	return time_t;
}
double f(double x, double y)
{
	double t = pow(x, 2) + 2 * y;
	return t;
}
double hx(double a, double b, double N)
{
	double x = (b - a) / (2 * N);
	return x;
}
double hy(double d, double c, double M)
{
	double x = (d - c) / (2 * M);
	return x;
}
double xi(double a, int i, double hx)
{
	return a + i * hx;
}
double yj(double b, int j, double hy)
{
	return b + j * hy;
}
double Simpsons(double a, double b, int n)
{
	double h, x1 = 0, x2 = 0;
	h = (b - a) / n;
	for (int i = 0; i <= n; ++i)
	{
		if (i % 2 == 0)
		x1 += funk(a + h * i);
		if (i % 2 == 1)
		x2 += funk(a + h * (i + 1));
	}

	double eror = pow(h, 4) * (a + h * n) / 180;

	return h / 3 * (funk(a) - funk(b) + 4 * x2 + 2 * x1);
}
double Trap(double a, double b, int n)
{
	double h, x1 = 0, x2 = 0;
	h = (b - a) / n;
	for (int i = 0; i <= n; ++i)
	{

			x1 += funk(a + h * i);

	}

	double eror = pow(h, 4) * (a + h * n) / 180;

	return h / 2 * (funk(a) + funk(b) + 2* x1 );
}
double Kub(double a, double b, double c, double d, int M, int N)
{
	double I = hx(a, b, N) * hy(c, d, M) / 9,sum=0;
	for (int i = 0; i < N-1; i++)
	{
		for (int j = 0; j < M-1; j++)
		{
			sum += f(xi(a, 2*i, hx(a, b, N)),yj(c,2*j,hy(c,d,M)))+4* f(xi(a, (2 * i)+1, hx(a, b, N)), yj(c, 2 * j, hy(c, d, M)))+ f(xi(a, (2 * i) + 2, hx(a, b, N)), yj(c, 2 * j, hy(c, d, M))) + 4*f(xi(a, (2 * i) , hx(a, b, N)), yj(c, (2 * j)+1, hy(c, d, M))) +16 * f(xi(a, (2 * i) + 1, hx(a, b, N)), yj(c, (2 * j)+1, hy(c, d, M))) + 4 * f(xi(a, (2 * i) + 2, hx(a, b, N)), yj(c, (2 * j)+1, hy(c, d, M))) + f(xi(a, 2 * i, hx(a, b, N)), yj(c, (2 * j) + 2, hy(c, d, M))) + 4 * f(xi(a, (2 * i) + 1, hx(a, b, N)), yj(c, (2 * j) + 2, hy(c, d, M))) + f(xi(a, (2 * i) + 2, hx(a, b, N)), yj(c, (2 * j) + 2, hy(c, d, M)));
		}
	 
	}
	double res = I * sum;
	return res;
}




void main()
{
	setlocale(0, " ");
	double eps = 0.00001, a = 2, b = 3.104;
	int p = 0,n=2;
	cout << "Выберете операцию(для выбора введите номер операции):" << "\n" << "1) Формула трапеций" << "\n" << "2) Формула Симпсона" << "\n" << "3) Кубаторная формула симпсона" << "\n";
	cin >> p;
	if (p == 1)
	{
		double Integ1, Integ2;
		Integ1 = Trap(a, b, n);
		do {
			Integ2 = Integ1;
			n = n * 2;
			Integ1 = Trap(a, b, n);
		} while (abs(Integ1 - Integ2) >= 3 * eps);
		cout << "Интеграл: " << Integ1;
	}
	if (p == 2)
	{
		double Integ1, Integ2;
		Integ1 = Simpsons(a, b, n);
		do {
			Integ2 = Integ1;
			n = n * 2;
			Integ1 = Simpsons(a, b, n);
		} while (abs(Integ1 - Integ2) >= 15 * eps);
		cout << "Интеграл: " << Integ1;
	}
	if (p == 3)
	{
		double a=0, b=2, c=0, d=1;
		int M, N;
		cout << "Введите M:" << "\n";
		cin >> M;
		cout << "Введите N:" << "\n";
		cin >> N;
		double res = Kub(a, b, c, d, M, N);
		cout << "Результат вычислений:" << res << endl;


	}

}
