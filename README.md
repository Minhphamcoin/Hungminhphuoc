# Hungminhphuoc
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace BT1_2._2_
{
    public class PhanSo : IComparable
    {
        private int tuso;
        private int mauso;
        //constructor PhanSo
        public PhanSo(int tuso, int mauso)
        {
            this.tuso = tuso;
            this.mauso = mauso;
        }
        public PhanSo(int soTN)
        {
            tuso = soTN;
            mauso = 1;
        }
        public int TuSo
        {
            get
            {
                return TuSo;
            }
            set
            {
                tuso = value;
            }
        }
        public int MauSo
        {
            get
            {
                return mauso;
            }
            set
            {
                if (value != 0)
                    mauso = value;
                else
                    mauso = 1;
            }
        }
        public static implicit operator PhanSo(int soTN)
        {
            return new PhanSo(soTN);
        }
        public static explicit operator float(PhanSo phanso)
        {
            return (float)phanso.tuso / phanso.mauso;
        }
        public static bool operator ==(PhanSo lhs, PhanSo rhs)
        {
            if (lhs.tuso == rhs.tuso && lhs.mauso == rhs.mauso)
            {
                return true;
            }
            return false;
        }
        public static bool operator !=(PhanSo lhs, PhanSo rhs)
        {
            return !(lhs == rhs);
        }
        public static bool operator >(PhanSo lhs, PhanSo rhs)
        {
            if ((float)lhs > (float)rhs)
            {
                return true;
            }
            return false;
        }
        public static bool operator < (PhanSo lhs, PhanSo rhs)
        {
            if ((float)lhs < (float)rhs)
            {
                return true;
            }
            return false;
        }

        public override bool Equals (object o)
        {
            if (!(o is PhanSo))
            {
                return false;
            }
            return this == (PhanSo)o;
        }
        public static PhanSo operator +(PhanSo lhs, PhanSo rhs)
        {
            int temp1 = lhs.tuso * rhs.mauso;
            int temp2 = rhs.tuso * lhs.mauso;
            PhanSo kq = new PhanSo(temp1 + temp2, lhs.mauso * rhs.mauso);
            return kq.RutGonPhanSo();
        }
        public static PhanSo operator - (PhanSo lhs, PhanSo rhs)
        {
            int temp1 = lhs.tuso * rhs.mauso;
            int temp2 = rhs.tuso * lhs.mauso;
            PhanSo kq = new PhanSo(temp1 - temp2, lhs.mauso * rhs.mauso);
            return kq.RutGonPhanSo();
        }
        public static PhanSo operator * (PhanSo lhs, PhanSo rhs)
        {
            PhanSo kq = new PhanSo(lhs.tuso * rhs.tuso, lhs.mauso * rhs.mauso);
            return kq.RutGonPhanSo();
        }
        public static PhanSo operator /(PhanSo lhs, PhanSo rhs)
        {
            PhanSo kq = new PhanSo(lhs.tuso * rhs.mauso, lhs.mauso * rhs.tuso);
            return kq.RutGonPhanSo();
        }
        public override string ToString()
        {
            string s = tuso.ToString() + "/" + mauso.ToString();
            return s;
        }
        public int CompareTo(PhanSo ps)
        {
            if ((float)this > (float)ps)
                return 1;
            else if ((float)this < (float)ps)
                return -1;
            else
                return 0;
        }
        //Yeu cau ve giao dien IComparable
        public int CompareTo(Object o)
        {
            PhanSo ps = (PhanSo)o;
            return this.CompareTo(ps);
        }
        private int USCLN(int x, int y)
        {
            while (x != y)
            {
                if (x > y)
                    x -= y;
                else
                    y -= x;
            }
            return x;
        }
        public PhanSo RutGonPhanSo()
        {
            int UCLN = USCLN(tuso, mauso);
                tuso = tuso / UCLN;
            mauso = mauso / UCLN;
            return new PhanSo(tuso, mauso);
        }
    }
}
