package amabze.aman.frag;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentTransaction;

import android.os.Bundle;
import android.view.MenuItem;
import android.widget.FrameLayout;

import com.google.android.material.bottomnavigation.BottomNavigationView;

public class MainActivity extends AppCompatActivity {

    private BottomNavigationView mMainNav;
    private FrameLayout mMainframe;

    private homeFragment HomeFragment;
    private dashFragment DashFragment;
    private profileFragment ProfileFragment;
    private TreeFragment treeFragment;




    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mMainNav=(BottomNavigationView)findViewById(R.id.main_nav);
        mMainframe=(FrameLayout)findViewById(R.id.main_frame);

        HomeFragment=new homeFragment();
        DashFragment=new dashFragment();
        ProfileFragment= new profileFragment();
        treeFragment=new TreeFragment();

        mMainNav.setOnNavigationItemReselectedListener(new BottomNavigationView.OnNavigationItemReselectedListener() {
            @Override
            public void onNavigationItemReselected(@NonNull MenuItem item) {

                switch (item.getItemId()){

                    case R.id.nav_home :
                        mMainNav.setItemBackgroundResource(R.color.colorPrimary);
                        setfragement(HomeFragment);
                        break;
                    case R.id.nav_dash :
                        mMainNav.setItemBackgroundResource(R.color.colorAccent);
                        setfragement(DashFragment);
                        break;
                    case R.id.nav_profile :
                        mMainNav.setItemBackgroundResource(R.color.colorPrimaryDark);
                        setfragement(ProfileFragment);
                        break;
                    case R.id.nav_tree :
                        mMainNav.setItemBackgroundResource(R.color.design_default_color_error);
                        setfragement(treeFragment);
                        break;






                }
            }

            private void setfragement(Fragment fragment) {
                FragmentTransaction fragmentTransaction = getSupportFragmentManager().beginTransaction();

                fragmentTransaction.replace(R.id.main_frame,fragment);
                fragmentTransaction.commit();

            }
        });


    }
}
