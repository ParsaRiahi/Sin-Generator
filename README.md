# Sin-Generator

#include <stdio.h>
#include <math.h>

int main(void)
{
    FILE *out;
    float samp = 0.0;

    out = fopen("sine.bin", "wb"); //w for write, file will be. but somehow wb is working

    float phi = 0.0;

    samp = 1.1;

    for(int i = 0; i < (48000 * 60 * 10); i++)
    {
        phi = phi + (i * 2 * M_PI / 48000.0) / 600.0;

        if(phi > (2 * M_PI))
        {
            phi = phi - (2 * M_PI);
        }
        
        samp = sin(phi);
        fwrite(&samp, sizeof(float), 1, out);
    }

    printf("done\n");

    fclose(out);
    return 0;
}

//do a sweep in an exponential curve
