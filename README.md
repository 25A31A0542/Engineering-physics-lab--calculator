# Engineering-physics-lab--calculator
Program project name 
#include <stdio.h>
#include <math.h>

#define Q 1.602e-19  // charge of electron in Coulombs

void ohmsLaw() {
    double V, I, R;
    int choice;
    printf("\n--- Ohm's Law ---\n");
    printf("Choose what to calculate:\n1. Voltage (V)\n2. Current (I)\n3. Resistance (R)\n");
    scanf("%d", &choice);

    if (choice == 1) {
        printf("Enter Current (A): "); scanf("%lf", &I);
        printf("Enter Resistance (Ω): "); scanf("%lf", &R);
        V = I * R;
        printf("Voltage = %.4lf V\n", V);
    } else if (choice == 2) {
        printf("Enter Voltage (V): "); scanf("%lf", &V);
        printf("Enter Resistance (Ω): "); scanf("%lf", &R);
        I = V / R;
        printf("Current = %.4lf A\n", I);
    } else if (choice == 3) {
        printf("Enter Voltage (V): "); scanf("%lf", &V);
        printf("Enter Current (A): "); scanf("%lf", &I);
        R = V / I;
        printf("Resistance = %.4lf Ω\n", R);
    }
}

void kinematics() {
    double u, a, t, v, s;
    printf("\n--- Kinematics ---\n");
    printf("Enter initial velocity u (m/s): "); scanf("%lf", &u);
    printf("Enter acceleration a (m/s^2): "); scanf("%lf", &a);
    printf("Enter time t (s): "); scanf("%lf", &t);

    v = u + a * t;
    s = u * t + 0.5 * a * t * t;

    printf("Final velocity v = %.4lf m/s\n", v);
    printf("Displacement s = %.4lf m\n", s);
}

void optics() {
    double f, u, v, lam, a, D, beta;
    printf("\n--- Optics ---\n");
    printf("Enter focal length f (m): "); scanf("%lf", &f);
    printf("Enter object distance u (m): "); scanf("%lf", &u);
    v = 1 / ((1/f) - (1/u));
    printf("Image distance v = %.4lf m\n", v);

    printf("\nDiffraction calculation:\n");
    printf("Enter wavelength λ (m): "); scanf("%lf", &lam);
    printf("Enter slit width a (m): "); scanf("%lf", &a);
    printf("Enter screen distance D (m): "); scanf("%lf", &D);
    beta = lam * D / a;
    printf("Fringe spacing β = %.6lf m\n", beta);
}

void hallEffect() {
    double VH, I, B, t, RH, n;
    printf("\n--- Hall Effect ---\n");
    printf("Enter Hall voltage V_H (V): "); scanf("%lf", &VH);
    printf("Enter Current I (A): "); scanf("%lf", &I);
    printf("Enter Magnetic field B (T): "); scanf("%lf", &B);
    printf("Enter sample thickness t (m): "); scanf("%lf", &t);

    RH = VH * t / (I * B);
    n = 1 / (Q * RH);

    printf("Hall coefficient R_H = %.6e m^3/C\n", RH);
    printf("Carrier concentration n = %.6e 1/m^3\n", n);
}

void resonance() {
    double L, C, R, f0, Qf, BW;
    printf("\n--- Resonance (LCR circuit) ---\n");
    printf("Enter Inductance L (H): "); scanf("%lf", &L);
    printf("Enter Capacitance C (F): "); scanf("%lf", &C);
    printf("Enter Resistance R (Ω): "); scanf("%lf", &R);

    f0 = 1 / (2 * M_PI * sqrt(L * C));
    Qf = (1/R) * sqrt(L/C);
    BW = f0 / Qf;

    printf("Resonant frequency f0 = %.4lf Hz\n", f0);
    printf("Quality factor Q = %.4lf\n", Qf);
    printf("Bandwidth Δf = %.4lf Hz\n", BW);
}

int main() {
    int choice;
    do {
        printf("\n=== Engineering Physics Lab Calculator ===\n");
        printf("1. Ohm's Law\n");
        printf("2. Kinematics\n");
        printf("3. Optics\n");
        printf("4. Hall Effect\n");
        printf("5. Resonance (LCR)\n");
        printf("0. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1: ohmsLaw(); break;
            case 2: kinematics(); break;
            case 3: optics(); break;
            case 4: hallEffect(); break;
            case 5: resonance(); break;
            case 0: printf("Exiting...\n"); break;
            default: printf("Invalid choice!\n");
        }
    } while(choice != 0);

    return 0;
}
