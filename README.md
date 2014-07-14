## SM Transitional API Helpers

A set of helper include files for cleverly (or abusively) working with the SM transitional API.

## Usage

1. Include thelpers:

  ```sourcepawn
  #define GAME_TF2
  #include <thelpers/thelpers>
  ```
  
2. Go wild

  ```sourcepawn
  public void OnClientPutInServer( int client )
  {
    CBasePlayer player = CBasePlayer( client );
    
    char steamId[ 128 ];
    player.GetSteamID( steamId, sizeof( steamId ) );
    
    PrintToServer( "%N's steam id: %s", player.Index, steamId );
    
    // do some tf2 specific stuff
    CTFPlayer tfPlayer = CTFPlayer:player;
    tfPlayer.SetClass( TFClassType_Medic );
    
    // we didn't like them anyway
    ServerCommand( "sm_kick #%d", player.UserID );
  }
  ```

## Considerations

- This library will be changing rapidly and often. Expect breaking changes.
- SM's transitional syntax is exerimental and thus has the potential to break us. Expect more breaking changes.
